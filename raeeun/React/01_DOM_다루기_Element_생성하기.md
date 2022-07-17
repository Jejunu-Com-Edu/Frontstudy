# DOM 이란? 
---
+ DOM (Document Object Model)
+ 문서를 **논리 트리**로 표현

+ 브라우저가 이해하는 element 의 원형이다!

[참고](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model)

<br>

# Vanilla JS 란?
---
+ 순수 자바스크립트

+ 특정 라이브러리나 프레임워크를 사용하지 않은 그 자체의 자바스크립트

[여기에서 js 체험 가능!](https://www.w3schools.com/)

위 사이트에서 js뿐만 아니라 html, css는 물론 sql, bootstrap까지 연습해볼 수 있다.

<br>

# DOM과 Element 다루기
---
## 하고 싶은 것
1. 부모 element와 자식 element를 각각 생성
2. 부모 element에 자식 element를 append

<br>

## Html code
```html
<body>
  <div id="root"></div>
</body>
```
자식 element를 생성하고 위 ```<div>```를 가지는 부모 element 안에  넣을 것이다.

<br>

## Javascript
```html
<script>
  const rootElement = document.getElementById("root");
  const element = document.createElement("h1");
  element.textContent = "Hello, javascript!";
  rootElement.appendChild(element);
</script>
```
+ ```document.createElement('태그 이름')``` : 태그 이름에 해당하는 태그를 생성

+ ```요소1.appendChild(요소2)``` : '요소1' 의 자식으로 '요소2' 를 추가
<br>

![](https://velog.velcdn.com/images/reyang/post/5a93b111-cecb-43a0-907b-7f7979dc25a2/image.png)

![](https://velog.velcdn.com/images/reyang/post/c1c28469-68b7-445d-8114-0c45600fd201/image.png)
하고 싶은 것을 성공했다.

<br>

## React & ReactDOM

다음은 React와 ReactDOM을 사용하여 하고 싶은 것을 성공해보겠다.
<br>
```html
<script>
  const rootElement = document.getElementById("root");
  const element = React.createElement("h1", {children : "Hello, react!"});
  ReactDOM.render(element, rootElement);
</script>
```
+ ```React.createElement('태그 이름')``` : 태그 이름에 해당하는 태그를 생성

+ ```ReactDOM.render(요소1, 요소2)``` : '요소2' 의 자식으로 '요소1' 을 추가

![](https://velog.velcdn.com/images/reyang/post/9f600cd7-0460-4ad9-a5a7-9620091f97ec/image.png)
![](https://velog.velcdn.com/images/reyang/post/517393a6-33ee-46f4-bbbb-223b547d77f4/image.png)
하고 싶은 것을 성공했다..!

<br>

## React.createElement
 + react 에서 태그를 생성해준다.

+ 인자 구성 : ```React.createElement( 태그 이름, props, 자식 요소 )```
	- 여기서 props는 완전 짱중요하다...
	- 해당 인자를 바꾸면서 위의 코드를 수정할 수 있다.

```javascript
const element = React.createElement("h1", {children : "Hello, react!"});
```
```javascript
const element = React.createElement("h1", null, "Hello, react!");
```
위 두개의 코드는 똑같은 결과를 나타낸다.

props라는 것으로 children 값에 "Hello, react!"를 줄 수도 있고,
자식 요소를 받는 세 번째 인자에 "Hello, react!"를 넣을 수도 있다.

<br>

## props?
그럼 props는 대체 무엇일까
props는 객체 형태로 전달되는 인자라고 생각하면 된다.

예를 들어, ```React.createElement```를 할 때, 이런 것도 가능하다.
```javascript
const element = React.createElement("h1", {
  className : "title",
  children : "Hello, react!"
});
```
```html
<!-- element의 결과 -->
<h1 className="title">Hello, react!</h1>
```
props를 줌으로써 태그를 생성함과 동시에 속성값을 줄 수 있다.
엄청 편하다..

참고로, props의 children 값보다 세 번째 인자(자식 요소)의 우선순위가 높다.
```javascript
const element = React.createElement("h1", {
  children : "Hello, react!"
}, "Hello, react!!!");
```
다시 말해서, 위 코드를 실행하게 되면 ```Hello, react!!!```가 나타나게 된다.

<br>
