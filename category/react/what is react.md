# React란?

Facebook에서 만든 UI 설계를 위한 오픈 소스 Javascript 라이브러리로써, 컴포넌트를 생성하고  
상태와 속성값을 다루며 이벤트 리스너를 도구로 사용한다.

React를 사용한 Application _(이하 App)_ 이 브라우저에 rendering될 때, HTML의 실제 소스 코드 내에서는 HTML 관련 코드들이 다뤄지지 않는다. 다만, React 내에 존재하는 가상의 DOM _(virtual DOM)_ 의 컴포넌트 내에 있는 HTML을 브라우저로 pass 시켜 수많은 데이터와 코드들을 효율적으로 설계하고 렌더링할 수 있게 해준다.

> HTML과 Javascript의 기능을 결합한 JSX(Javascript Syntax Extension)을 사용한다.

## Component

- 컴포넌트는 기본적으로 HTML을 반환하는 함수, 더 나아가 클래스 형태를 띄고 있는 하나의 부품이다.
- React 내의 App은 한번에 하나의 컴포넌트만 rendering 할 수 있기 때문에 App 내에 다른 컴포넌트들을 배치시켜  
  이루어진 하나의 컴포넌트를 최종 브라우저에 rendering 시킨다.
- 기본적으로 컴포넌트들은 대문자로 시작한다는 convention을 가지고 있다.
- import 명령을 이용하여 다른 파일에서 컴포넌트를 가져와 쓰고 싶을 때, from 뒤의 "./blah/blah" 는  
  "동일 디렉토리 ( . ) 의 하위 ( / )에 위치한 컴포넌트를 가져온다는 의미이다.

## Props

- 한 컴포넌트 안에 다른 컴포넌트가 위치할 때 밖에 위치한 것은 부모, 안에 위치한 것은 자식 컴포넌트이다.
  - 부모 안에서 자식의 props(properties)와 value의 값을 설정할 수 있고 자식 컴포넌트로 정보를 보내면  
    자식은 그것을 props라는 '객체'형태의 인자로 받는다.
  - map이나 여러 메소드를 사용해 동일한 형태의 HTML을 리턴하게 될 경우 key값을 부여해 고유한 속성을 부여한다.  
    (react가 구별할 수 있도록)
