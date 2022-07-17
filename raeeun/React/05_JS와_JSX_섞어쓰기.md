## 하고 싶은 것
+ props의 속성값에 따라서 다른 엘리먼트를 생성하고 싶다!

+ 예를 들어, text라는 props의 속성값의 첫번째 문자가 대문자라면 ```<h1>```로 나타내고 아니라면 ```<h3>```로 나타내고 싶다

<br>

## 코드

```jsx
const Text = ({ text }) => {
  if (text.charAt(0) === text.charAt(0).toUpperCase()) {
    return <h1>{text}</h1>;
  else {
    return <h3>{text}</h3>;
  }
};

const element = (
  <>
    <Text text="Text" />
    <Text text="text" />
  </>
);
```
Text라는 custom element를 만들어
element에서 하나는 대문자값, 하나는 소문자값을 주고 찍어냈다.

여기서 짚고 넘어가야 할 점은, js와 jsx를 섞어쓰고 있다는 것이다.
```jsx
return (
  <h1>
    {/* jsx */}
    {text}	{/* js */}
  </h1>		/* jsx */
);
```
Html에서도 ```<style>```안에서 CSS 코드를, ```<script>```안에서 JavaScript 코드를 작성할 수 있는 것 처럼 html, css, js를 섞어쓸 수 있다.

이와 비슷하게 jsx안에서 js와 jsx를 섞어쓸 수 있다는 개념이다.
이것을 **Interpolation**이라고 한다.

<br>

## 결과
![](https://velog.velcdn.com/images/reyang/post/5da1c64e-092e-44b0-ae82-da787cc37b86/image.png)


<br> 

## 하고 싶은 것 2
+ number라는 props의 값이 짝수일때만 ```<h1>```으로 나타내고 싶다.


<br>

## 코드 2
```jsx
function Number({number}) {
  return ( number % 2 === 0 ? <h1>{number}</h1> : <h3>{number}</h3> );
}

const element = (
  <> 
    <Number number={1} />
    <Number number={2} />
    <Number number={3} />
    <Number number={4} />
  </>
);
```
<br>

## 결과 2
![](https://velog.velcdn.com/images/reyang/post/40e344e2-c6fc-443c-b73a-126632e16d47/image.png)


<br>

## 코드 2-2
```jsx
function Number({number, selected}) {
  return ( selected ? <h1>{number}</h1> : <h3>{number}</h3> );
}

const element = (
  <> 
    <Number number={1} />
    <Number number={2} selected={true} />
    <Number number={3} />
    <Number number={4} selected={true} />
  </>
);
```
selected라는 props를 추가해서 선택된 요소들만 다르게 나타나도록 만든 코드이다.

이를 응용하면 더 다양한 코드를 만들 수 있다.

<br>

## 코드 2-3
```jsx
function Number({number, selected}) {
  return ( selected ? <h1>{number}</h1> : <h3>{number}</h3> );
}

const element = (
  <>
    {[1, 2, 3, 4, 5, 6, 7, 8, 9, 10].map((number) => (
      <Number number={number} selected={number === 3} />
    ))}
  </>
);
```
<br>

## 결과
![](https://velog.velcdn.com/images/reyang/post/8b66e53d-bf88-4f97-af4a-73c2b8346bce/image.png)


<br>

