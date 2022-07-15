# CodeSandBox 란?
---
+ 프론트엔드 코드를 작성하면서 여러가지를 시도해볼 수 있는 사이트

+ React 등 다양한 환경에 대한 기본 설정이 되어있다.

[바로가기](https://codesandbox.io/)

리액트를 공부하면서 이 CodeSandBox를 사용할 생각이다.

<br>

## 사용법

![](https://velog.velcdn.com/images/reyang/post/09fce8e6-8bfb-4f26-8741-241a98754bbc/image.png)

CodeSandBox 사이트에 들어간다.
우측 상단의 Create Sandbox 를 클릭

![](https://velog.velcdn.com/images/reyang/post/111e1782-81ea-4181-be1d-ba37e06861f9/image.png)
그럼 해당 창이 뜨는데 원하는 환경을 선택해주면 그에 맞게 설정된 편집창이 뜨게 된다.
나는 ```<style>```과 ```<script>```코드로 css, js가 모두 가능한 html 파일 환경을 생성해주기 위해 static으로 선택했다.

<br>

# CDN 이란?
---
+ CDN (Content Delivery Network)

+ 웹에서 사용되는 다양한 리소스를 저장하여 제공하는 시스템

<br>

### CDN이 왜 필요한가?
> CDN을 사용하지 않을 경우 오리진 서버가 정보를 복제 및 저장한 다음 사용자가 웹에 접속하는 곳까지 디지털 콘텐츠를 가져가야 하기 때문에 인터넷 속도가 느려질 수 있습니다.

[출처](https://www.akamai.com/ko/our-thinking/cdn/what-is-a-cdn)

<br>

# React CDN 불러오기
---

[React를 제공하는 CDN](https://ko.reactjs.org/docs/cdn-links.html)
![](https://velog.velcdn.com/images/reyang/post/43df83ca-c310-49c1-860b-cbda25714c86/image.png)


위 링크에 들어가면 다음과 같은 화면을 볼 수 있다.
해당 링크는 UNPKG에서 제공되는 CDN 링크이다.

<br>

## UNPKG ?
+ CDN url들을 통일시켜주는 CDN 링크 모음 사이트 (라고 이해했습니다.)
+ npm에서 제공되는 모든 JavaScript에 대한 CDN 제공!

<br>

쉽게 말해, 아무런 설정도 되어있지 않은 편집환경에서 React 또는 ReactDOM를 사용하고 싶다면?
```html
<script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
```
UNPKG이 정의한 CDN url을 포함하는 해당 코드를 추가하면 해결된다!

<br>
