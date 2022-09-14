# Element.getBoundingClientRect()

**```Element.getBoundingClientRect()```** 메서드는 엘리먼트의 크기와 뷰포트에 상대적인 위치 정보를 제공하는 DOMRect 객체를 반환합니다.

## 구문
```js
domRect = element.getBoundingClientRect();
```

## 값
반환 값은 padding과 border-width를 포함해 전체 엘리먼트가 들어 있는 가장 작은 사각형인 ```DOMRect``` 객체입니다. ```left```, ```top```, ```right```, ```bottom```, ```x```, ```y```, ```width```, ```height``` 프로퍼티는 전반적인 사각형의 위치와 크기를 픽셀 단위로 나타냅니다. ```width```와 ```height```가 아닌 다른 프로퍼티는 뷰포트의 top-left에 상대적입니다.
![](https://velog.velcdn.com/images/reyang/post/b2641ae1-b24d-47be-aeca-5d05445ec873/image.png)

<br>

[참고](https://developer.mozilla.org/ko/docs/Web/API/Element/getBoundingClientRect)

![](https://velog.velcdn.com/images/reyang/post/4234b991-fdf1-422c-be41-3192bd733cbe/image.png)
