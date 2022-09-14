# window.requestAnimationFrame()

**```window.requestAnimationFrame()```**은 브라우저에게 수행하기를 원하는 애니메이션을 알리고 다음 리페인트가 진행되기 전에 해당 애니메이션을 업데이트하는 함수를 호출하게 합니다. 이 메소드는 리페인트 이전에 실행할 콜백을 인자로 받습니다.


>**참고: 노트:** 다음 리페인트에서 그 다음 프레임을 애니메이트하려면 콜백 루틴이 반드시 스스로 requestAnimationFrame()을 호출해야합니다.



## 구문
```js
window.requestAnimationFrame(callback);
```

## 예시
```js
var start = null;
var element = document.getElementById('SomeElementYouWantToAnimate');
element.style.position = 'absolute';

function step(timestamp) {
  if (!start) start = timestamp;
  var progress = timestamp - start;
  element.style.left = Math.min(progress / 10, 200) + 'px';
  if (progress < 2000) {
    window.requestAnimationFrame(step);
  }
}

window.requestAnimationFrame(step);
```

<br>

[참고](https://developer.mozilla.org/ko/docs/Web/API/Window/requestAnimationFrame)

JavaScript로 웹 게임을 만드려는 도중에
키를 누르면 캐릭터가 모션을 하는 코드였는데 움직임이 더뎠다

이것을 해결하기 위해 게임을 렌더링해주는 renderGame이라는 함수를 만들고 나서 키를 누르면 캐릭터가 동작을 하도록 하는 함수를 넣어주었다.
그 후 window.requestAnimationFrame에 renderGame을 콜백함수로 넣어주니 정말 매끄럽게 동작한다.!!

키를 눌러야만 캐릭터가 동작하도록 하는 것이 아니라
renderGame이 무한으로 호출되다가 사용자가 키를 누르면 키에 맞는 동작을 하므로 딜레이가 없다

<br>
