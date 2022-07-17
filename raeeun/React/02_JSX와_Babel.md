# JSX 란?
---
```jsx
const element = <h1>Hello, jsx!</h1>;
```
+ 위 처럼 사용 가능

+ JavaScript를 HTML처럼 사용할 수 있다! (JavaScript의 확장 문법)

<br>

# JSX 사용하기 (태그에 속성값 주기)
---
## JavaScript Code
```javascript
// const rootElement = document.getElementById("root");
const element = React.createElement("h1", {
  className : "title"
}, "Hello, react!");
// ReactDOM.render(element, rootElement);
```
해당 JavaScript (React, ReactDOM 사용) 코드를 JSX를 사용해서 줄여보겠다.

<br>

## JSX Code

```jsx
// const rootElement = document.getElementById("root");
const element = <h1 className="title">Hello, react!</h1>;
// ReactDOM.render(element, rootElement);
```
보이듯, JSX를 사용한다면 편하게 element 생성이 가능하다.
하지만 해당 코드를 실행하면 아무런 결과도 나타나지 않는다.
이유는 'babel' 이라는 것에 있다.

<br>

# Babel 이란?
---
+ 자바스크립트를 다른 프로그래밍 언어로 옮기는 프로그램 (JavaScript Complier)

+ JSX를 실행시키려면 코드를 JS로 변환시켜주는 Babel이 필요하다!

[babel 사이트](https://babeljs.io/)

+ Babel을 사용하기 위해서 UNPKG에서 정의하는 babel CDN url을 코드에 포함시키자!

<br>

## CDN? UNPKG?
[>> CDN과 UNPKG 설명](https://velog.io/@reyang/React-00.-CodeSandBox-사용하기-with-CDN)

<br>

![](https://velog.velcdn.com/images/reyang/post/15838d11-bd2e-4b42-a7fa-c90df0491631/image.png)

[babel UNPKG CDN](https://babeljs.io/docs/en/babel-standalone) 링크에 들어가면 다음과 같은 화면을 볼 수 있다.
밑줄 친 부분이 Babel의 _CDN url_ 이다.

```html
<script scr="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```
위 코드를 추가해주면 이제 Babel을 통해 JSX형식의 코드를 JS로 변환할 수 있게 된다!!

참고로 JSX 코드를 작성한 script태그의 type속성에 "text/babel"을 넣어주어야 한다. (이 내용을 babel이 컴파일해줘~~ 라는 뜻~)
```html
// 예시

<script type="text/babel">
  // jsx 코드
<script>
```

<br>

# JSX 사용하기 2 (변수 사용하기)
---
JSX를 사용하면 편리한 점 : **변수를 사용할 수 있다!** (대박)

## JSX Code (원래)
```jsx
const rootElement = document.getElementById("root");
const element = <h1 className="title">Hello, react!</h1>;
// ReactDOM.render(element, rootElement);
```
위 코드를 수정하여 변수를 사용해서 나타내보겠다.

<br>

## JSX Code (수정)
```jsx
// const rootElement = document.getElementById("root");
const titleClassName = "title";
const text = "Hello, react!";
const element = <h1 className={titleClassName}>{text}</h1>;
// ReactDOM.render(element, rootElement);
```
수정 완료.
이렇게 해도 같은 결과가 나타난다!

```jsx
// const rootElement = document.getElementById("root");
const titleClassName = "title";
const text = "Hello, react!";
const customH1 = <h1 className={titleClassName}>{text}</h1>;
const element = customH1;
// ReactDOM.render(element, rootElement);
```
요것도 가능

<br>

또
```jsx
/*1*/ <h1 className={titleClassName}>{text}</h1>
/*2*/ <h1 className={titleClassName} children={text} />
```
2번 코드처럼 닫는 태그를 저렇게 줄여서 표현 가능하다!

<br>

# JSX 사용하기 3 (spread 연산자)
---
+ props를 분해하는 역할

+ ... 으로 표기

<br>

## props?
[props란](https://velog.io/@reyang/React-01.-DOM-다루기-Element-생성하기)

<br>

```jsx
// const rootElement = document.getElementById("root");
// const titleClassName = "title";
// const text = "Hello, react!";
const customH1 = <h1 className={titleClassName} children={text} />
// const element = customH1;
// ReactDOM.render(element, rootElement);
```
해당 코드를 props와 spread연산자(...)를 사용하여 수정해보겠다.

<br>

```jsx
// const rootElement = document.getElementById("root");
// const titleClassName = "title";
// const text = "Hello, react!";
const props = { className : titleClassName, children : text };
const customH1 = <h1 {...props} />
// const element = customH1;
// ReactDOM.render(element, rootElement);
```
수정 완료.
이렇게 props 앞에 붙은 spread연산자(...)는 props의 프로퍼티를 하나하나 분해해준다!
(대박)

<br>