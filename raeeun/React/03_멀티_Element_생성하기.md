# 멀티 Element 생성하기
---

### 하고 싶은 것
```html
  <div id="root"> <!-- react 코드를 추가해서 여기에 멀티 Element를 생성 --> </div>
```
```html
<!-- 원하는 결과 -->
  <div id="root">
    <h1>Hi</h1>
    <h3>Bye</h3>
    <h5>Children</h5>
  </div>
```
<br>

### 내가 생각한 답
```js
    <script type="text/babel">
      const rootElement = document.getElementById("root");
      const props = { children: ["Hi", "Bye", "Children"] };

      let element;
      for (let i = 1; i < 6; i+=2) {
        element += <h{i} {...props}.[i] />;
      }

      ReactDOM.render(element, rootElement);
    </script>
```
과연 결과는~
![](https://velog.velcdn.com/images/reyang/post/f3393ef1-ca19-4c1d-8ee7-0a3b806f7683/image.png)

굿~

생각해보니 React를 쓰지도 않았다.. (JSX만 씀)
```React.createElement``` 를 활용해서 다시 해보자

<br>

### 수정된 코드
```html
    <script type="text/babel">
      const rootElement = document.getElementById("root");
      const element = (
        <div className="box" children= {[
            React.createElement("h1", null, "Hi"),
            React.createElement("h3", null, "Bye"),
            React.createElement("h5", null, "Children")
          ]}
      	/>
   	  );
      ReactDOM.render(element, rootElement);
    </script>
```
children에 리스트를 넣어서 해결한 코드

하지만 이렇게되면 원했던 결과가 나오지 않는다.
```html
<!-- 코드 실행 결과 -->
  <div id="root">
    <div className="box">
      <h1>Hi</h1>
      <h3>Bye</h3>
      <h5>Children</h5>
    </div>
  </div>
```
원치 않았던 ```<div>```가 하나 더 생기기 떄문인데
```React.createElement```만 쓴다는 조건에서는 이게 최선이라고 한다 ㅠㅠ

이것을 해결하기 위해서 ```React.Fragment```를 사용할 수 있다.

<br>

# React.Fragment 사용하기
---
위 문제를 ```React.Fragment```를 사용해서 해결해보자
<br>

## React.Fragment
+ 여러 자식을 그룹화할때 사용

+ 이게 없었을때는 별도의 div태그를 사용해서 묶어줘야 했음

<br>



## 원래 코드
```jsx
// const rootElement = document.getElementById("root");
const element = (
  <div className="box" children= {[
      React.createElement("h1", null, "Hi"),
      React.createElement("h3", null, "Bye"),
      React.createElement("h5", null, "Children")
    ]}
  />
);
// ReactDOM.render(element, rootElement);
```

## 수정된 코드
```jsx
// const rootElement = document.getElementById("root");
const element = (
  <React.Fragment
    children= {[
      React.createElement("h1", null, "Hi"),
      React.createElement("h3", null, "Bye"),
      React.createElement("h5", null, "Children")
    ]}
  />
);
// ReactDOM.render(element, rootElement);
```
![](https://velog.velcdn.com/images/reyang/post/826192f9-a39f-4b35-8405-6233e55133af/image.png)
수정된 코드에서는 따로 ```<div>```태그가 추가되지 않은 것을 볼 수 있다.

근데 이 코드를 더 간결하게 만들수도 있다. (이게 진짜 대박)
```jsx
// 방법 1)
const element = (
        <React.Fragment>
          {[<h1>Hi</h1>, <h3>Bye</h3>, <h5>Children</h5>]}
        </React.Fragment>
      );
```
```jsx
// 방법 2)
const element = (
        <React.Fragment>
          <h1>Hi</h1>
          <h3>Bye</h3>
          <h5>Children</h5>
        </React.Fragment>
      );
```
```jsx
// 방법 3)
const element = (
        <>
          <h1>Hi</h1>
          <h3>Bye</h3>
          <h5>Children</h5>
        </>
      );
```
React에서는 React.Fragment를 생략하는 문법 (방법 3)도 제공해준다

<br>