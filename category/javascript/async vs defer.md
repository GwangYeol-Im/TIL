# Async vs defer의 차이점

HTML 파일과 javascript파일을 연결할 때 스크립트 페이지를 **언제 받아서 실행할 것인지** 선언하는 명령어라고 할 수 있다.

## 1. 보통의 스크립트 선언 (head 부분 선언)

```javascript
<!DOCTYPE html>
<html lang="en">
  <head>
    ...
    ...
    <script src="main.js"></script>
  </head>
```

> parsing HTML > fetching js > executing js > parsing the rest of the HTML

    스크립트 페이지를 내려받고 실행할 동안 html구조를 나타낼 수 없기 때문에 사용자 입장에서 시간이 오래걸린다.

## 2. body 끝 부분에 선언

```javascript
<!DOCTYPE html>
<html lang="en">
  <head>
  ...
  </head>

  <body>
    ...
    <script src="main.js"></script>
  </body>
</html>
```

> parsing HTML > page is ready > fetching js > executing js

    기본 html구조를 빠르게 가져오는 특징이 있지만 웹페이지가 js를 중심으로 하는 퍼포먼스 우선이라면
    사용자에게 좋지 않은 UX를 제공할 가능성이 있다.

## 3. head에 async을 선언하기.

```javascript
<!DOCTYPE html>
<html lang="en">
  <head>
    ...
    ...
    <script asyn src="main.js"></script>
  </head>
```

> parsing HTML & fetching js > executing js > parsing the rest of the HTML

    HTML을 분석하는 동안 비동기적(병렬)으로 js 스크립트 페이지를 내려받기 때문에 페이지 로딩 시간은 단축시킬 수 있지만 여전히 js가 실행되는 동안 html을 온전히 표현할 수 없고, js 내에서 queryselector를 이용한 dom요소를 처리할 때 html의 분석이 덜 끝나있기 때문에 호출 부분에서 문제가 생길 수 있다.

## 4. head에 defer 선언하기.

```javascript
<!DOCTYPE html>
<html lang="en">
  <head>
    ...
    ...
    <script defer src="main.js"></script>
  </head>
```

> parsing HTML & fetching js > page is ready > executing js

    HTML을 분석하는 동안 병렬적으로 js를 받고, 분석이 끝나면 바로 js를 실행하기 때문에
    여러 js 스크립트 페이지를 순서대로 실행하고 싶을 때에도 알맞은 방법이다.
