# this keyword 정리

### 1. 대부분 케이스에서 this의 value는 _함수가 어떻게 호출되었는지_ 에 따라 달라진다.

포괄적인 의미로 보자면 **this**는 선언된 함수나 변수가 호출되었을 때,  
호출된 execution context를 가리킨다고 볼 수 있다.

```javascript
console.log(this);
//Window {parent: Window, opener: null, top: Window, length: 1, frames: Window, …}
```

Global 영역은 Window라는 하나의 **커다란 객체**로 볼 수 있다.

```javascript
    var this.a = 32;
    console.log(Window.a);
    //32
```

window객체의 a프로퍼티에 값을 할당했기 때문에 this.a의 값은 32라는 것을 유추할 수 있다.

```javascript
const test = {
  prop: 42,
  func: function() {
    return this.prop;
  }
};

console.log(test.func());
// expected output: 42
```

때문에 console로 test.func()를 호출했을 때,  
func이 실행되는 context는 test라는 객체 내부이기 때문에 this의 값은 test로 인식된다.

### 2. bind 함수에 대하여

주로 함수를 선언할 때 .bind() 형태로 함수를 지정해주어 첫번째로 받는 인자를 execution context로 인식하게 해주는 메소드이다.

react의 경우 해당 컴포넌트 내의 render함수에서 this설정을 많이 하게 되는데,  
render 함수 내에서 함수를 선언하게 되는 경우 해당 함수 내에 this를 선언한다고 해도  
어느 execution context에서 호출되는지 알 수 없기 때문에 그 this는 undefined를 도출한다.

```js
    class App extends Component {
        render(){
            console.log(this); //App
                    function(){
                console.log(this); //undefined
            }
        }
    }
```

때문에 bind()를 이용하여 this의 값을 임의로 설정해줄 필요가 있다.

### this keyword 추가 정리

Reference: [Poiemaweb(화살표 함수)](https://poiemaweb.com/es6-arrow-function)

**_일반 함수의 경우 객체의 메소드, 생성자 함수를 제외한 모든 함수 (콜백, 내부함수 포함)은 전역(window)객체를 this로 받는다._**

하지만 화살표 함수의 경우 this에 바인딩할 객체가 정적으로 결정된다.

화살표 함수의 this는 언제나 상위 스코프의 this를 가리킨다.  
때문에 유의사항으로 객체의 메소드 or 생성자 함수로써의 경우에는 화살표 함수를 잘못 쓴다면 혼란을 가중시킬 우려가 있다.
