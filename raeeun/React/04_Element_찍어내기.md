## 하고 싶은 것
+ 똑같은 엘리먼트를 계속 찍어내기
```html
<h1>Hi</h1>
<h3>hi</h3>
```
를 찍어내보자

<br>

## 코드
```jsx
const rootElement = document.getElementById("root");

const paint = () => (
  <>
    <h1>Hi</h1>
    <h3>hi</h3>
  </>
);

const element = (
  <>
    {paint()}
    {paint()}
    {paint()}
  </>
);

ReactDOM.render(element, rootElement);
```

<br>

## 결과
![](https://velog.velcdn.com/images/reyang/post/706fd888-065f-431b-bd7e-8f4caff14ef7/image.png)
성공적.

<br>

## 활용하기 1 (인자 주기)
```jsx
const rootElement = document.getElementById("root");

const paint = (title, description) => (
  <>
    <h1>{title}</h1>
    <h3>{description}</h3>
  </>
);

const element = (
  <>
    {paint("Good", "good")}
    {paint("Bad", "bad")}
    {paint("Soso", "soso")}
  </>
);

ReactDOM.render(element, rootElement);
```
![](https://velog.velcdn.com/images/reyang/post/5d421b88-843b-48a2-adc8-f894ae3fbe31/image.png)

<br>


## 활용하기 2 (태그로 함수 호출)
```jsx
const rootElement = document.getElementById("root");

// paint -> Paint
// 함수 이름 대문자로 바꿔야함
const Paint = ({title, description}) => (
  <>
    <h1>{title}</h1>
    <h3>{description}</h3>
  </>
);

const element = (
  <>
    <Paint title="Haha" description="haha" />
    <Paint title="Hoho" description="hoho" />
    <Paint title="Huhu" description="huhu" />
  </>
);

ReactDOM.render(element, rootElement);
```
![](https://velog.velcdn.com/images/reyang/post/79b54907-1c81-44eb-b9e5-78c77ff63d3a/image.png)

+ 이때, paint -> Paint 로 이름을 바꿔준 이유는
```<p>```나 ```<span>```같은 태그로 착각하지 않기 하기 위함! (custom-element 라고도 한다)

<br>

## 활용하기 3 (children 사용)
```jsx
const rootElement = document.getElementById("root");

const Paint = ({ title, description, children }) => (
        <>
          <h1>{title}</h1>
          <h3>{description}</h3>
          {children}
        </>
      );

      const element = (
        <>
          <Paint title="Haha" description="haha">
            hahaha!!
          </Paint>
          <Paint title="Hoho" description="hoho">
            hohoho!!
          </Paint>
          <Paint title="Huhu" description="huhu">
            huhuhu!!
          </Paint>
        </>
      );

ReactDOM.render(element, rootElement);
```
+ ```React.Fragment```(<>)에 있는 자식 요소를 ```<Paint>```가 자동대로 children 인자로 받음! (신기)

```jsx
const Paint = ({ title, description, children }) ...
```
이 부분의 ```{title, description, children}```은 props가 된다!


![](https://velog.velcdn.com/images/reyang/post/b1194d7d-fa58-405e-89c8-8683ae830a88/image.png)

<br>

+ 참고로 children은 제한이 없다! 무한대로 늘어나도 상관 X

<br>
