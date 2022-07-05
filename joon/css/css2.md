# 연결 선택자
둘 이상의 선택자를 연결해서 스타일이 적용될 요소가 어느 부분인지 지정하는 것. 선택자를 둘 이상 조합하므로 '조합 선택자'라고도 하고 '콤비네이션 선택자'등 이라고 부름

<br>
<br>

## 하위 요소에 스타일을 적용하는 하위 선택자와 자식 선택자
현재 요소를 기준으로 바로 한 단계 아래 요소는 자식요소, 그 자식 요소의 한 단계 아래는 손자요소라고 함.

### 하위선택자
부모 요소에 포함된 하위 요소를 모두 선택하며 자손 선택자라고도 함. 즉, 자식 요소뿐만 아니라 손자 요소, 손자의 손자 요소 등 모든 하위 요소까지 전부 적용됨.
```
section p { 
(상위요소) (하위요소)
```

```html
<style>
  section p {
    color : blue;
  }
</style>

<section>
  <h1>예약 방법 & 사용 요금</h1>
  <p>아직 온라인 예약 신청이 </p>
  <div>
    <p> 가족실 </p>
    <p>도미토리</p>
  </div>
</section>
```

### 자식 선택자
하위 선택자와 다르게 자식 요소에만 스타일을 적용하는 선택자로, 다음과 같이 두 요소 사이에 '>'기호를 표시해 부모 요소와 자식 요소를 구분함.

```
부모요소 > 자식요소
```
```css
section > p {

}
```

### 인접 형제 선택자
형제 요소 중에서 첫 번째 동생 요소만 선택하는 것을 인접 형제 선택자라고 함. 인접 형제 선택자를 정의할 때는 다음 기본형과 같이 요소 사이에 '+'기호를 표시함
```
요소1 + 요소2
```
```css
h1 + p {
  color:blue;
}
```

```html
<style>
h1 + p {
  background-color: #222;
  color: #fff;
}
</style>
<h1>예약 방법 & 이용 요금</h1>
<p>아직 온라인 예약</p> <!-- h1 요소의 형제 요소 중에서 첫 번째 형제인 p 요소에 적용-->
<p>가족실(2~4인)</p>
```

### 형제 선택자
형제 요소의 스타일을 정의하는데 인접 형제 선택자와 달리 모든 형제 요소에 적용됨. 형제 선택자를 정의할 때 첫 번째 요소와 두 번째 요소 사이에 '~'기호를 표시함.
```css
h1 ~ p {
  color: blue;
}
```
```html
<style>
  h1 ~ p{
    background-color: #222;
    color: #fff;
  }
</style>
  <h1> 예약 방법 & 이용 요금</h1>
  <p>123</p>
  <p>456</p>
  <p>789</p>
```

## 속성 선택자
태그 안에서 사용하는 속성값에 따라 요소를 선택 하는 역할을 함. 속성값의 조건에 따라 특정 부분만 선택하기 쉬우므로 상황에 맞는 스타일을 지정하기 쉬움
```css
a[href]{

}
```
첫 번째 a 요소에는 href 속성이 없으므로 스타일이 적용되지 않음
```html
<style>
  a[href]{
    background: yellow;
    border: 1px solid #ccc;
    font-weight: normal;
  }
</style>

<ul>
  <li><a>메인 메뉴 : </a></li>
  <li><a href="#">메뉴 1</a></li>
  <li><a href="#">메뉴 2</a></li>
  <li><a href="#">메뉴 3</a></li>
</ul>
```

### 특정 속상값이 있는 요소를 선택하는 [속성=속성값] 선택자
[속성 = 속성값]선택자는  주어진 속성과 속성값이 일치하는 요소를 찾아 스타일을 지정할 때 사용함. 대괄호([])안에 속성과 속성값을 넣고 그 사이에 '='기호를 표시함.
```css
a[target = _blank]{

}
```
```html
<style>
a[target="_blank"]{
  padding-right: 30px;
  background: url(images/newwindow.png) no-repeat center right;
}
</style>
<ul>
  <li><a href="https://html.spec.whatwg.org" target="_blank">HTML</a></li> <!-- a 요소 중에서 href속성값이 _blank인 요소에만 적용>-->
  <li><a href="https://html.spec.whatwg.org" >CSS</a></li>
  <li><a href="https://html.spec.whatwg.org" >JS</a></li>
```

### 여러 값 중에서 특정 속상값이 포함된 속성 요소를 선택하는 [속성~=값] 선택자
[속성~=값] 선택자는 여러 속성값 중 에서 해당 속성값이 포함된 요소를 선택함. 이 선택자는 속성이 하나면서 속성값이 여러 개일 때 특정 속성값을 찾는데 편리함.
```css
[class ~= button]{

}
```
```html
<style>
  [class ~= "button"]{ /* class  속성 값에 button이 포함된 요소를 찾는 선택자 */
    box-shadow: rgba(0,0,0, 0.4) 4px 4px;
    border-radius: 5px;
  }
</style>
<ul>
  <li><a href="#" class="flat">메뉴 1</a></li>
  <li><a href="#" class="flat">메뉴 2</a></li>
  <li><a href="#" class="button">메뉴 3</a></li>
  <li><a href="#" class="flat button">메뉴 4</a></li>
</ul>
```

### 특정 속성값이 포함된 속성 요소를 선택하는[속성 |= 값] 선택자
[속성 |= 값]선택자는 특정 속성값이 포함된 속성에 스타일을 적용함. 지정한 값과 정확하게 일치하거나 지정한 값을 포함해서 하이픈으로 연결된 단어도 선택됨
```css
a[title |= us]{

}
```

### 특정 속성값으로 시작하는 속성 요소를 선택하는[선택 ^= 값]
속성값이 정확하게 일치하지 않더라도 지정한 속성값으로 시작하는 요소를 찾으려면 [속성^= 값]선택자를 사용함.
예를 들어 title 속성값이 eng로 시작하는 a 요소를 찾는다면 다음과 같이 작성함.
```css
a[title ^= eng]{

}
```

### 특정한 값으로 끝나는 속성의 요소를 선택하는 [속성$= 값] 선택자
[속성 ^= 값]이 지정한 속성값으로 시작하는 요소를 선택했다면 [속성$=값]선택자는 지정한 속성값으로 끝나는 요소를 선택함. 예를 들어 링크한 파일 이름의 마지막 단어가 xls인 요소를 찾는다면 다음과 같이 작성함.
```css
[href $= xls]{

}
```

### 일부 속성값이 일치하는 요소를 선택하는 [속성*=값] 선택자
[속성 *= 값]선택자는 속성값이 어느 위치에 있든지 지정한 속성값이 포함되어 있다면 해당 요소를 선택함. 예를 들어 href 속성값 중에 'w3'가 포함된 요소를 선택한다면 다음과 같이 작성함.
```css
[href *= w3]{

}
```
```html
<style>
  a[href *= w3]{
    background: blue;
    color: white;
  }
</style>

<p>(아래 링크 중에서 배경색이 파란색인 링크는 W3C 사이트로 연결됩니다.)</p>

<ul>
  <li><a href="http://html.spec.whatwg.org/">HTML 표준안 사이트</a></li>
  <li><a href="http://html.spec.whatwg.org/">HTML 지원 여부 체크</a></li>
  <li><a href="http://www.w3.org/TR/css3-mediaqueries">미디어쿼리</a></li> <!--href의 속성값 중에서 "w3"가 일치하므로 스타일을 적용-->
</ul>
```

## 가상 클래스와 가상 요소
선택자로도 스타일을 지정하기 어려운 대상이 있음. 예를 들어 몇 번째 항목을 지정하거나, 단락의 첫 번째 글자만 지정할 경우입니다. 이럴때는 클래스 이름 앞에 콜론(:)을 1개만 붙여 표시하는 가상 클래스와 2개(::)를 붙여 표시하는 가상 요소를 사용하면 해결할 수 있음.
<br>
<br>

### 사용자 동작에 반응하는 가상 클래스
사용자가 웹 요소를 클릭하거나 마우스 포인터를 올려놓는 등 특정 동작을 할 때 스타일을 바꾸고 싶을때 가상 클래스 선택자를 사용함.

1. 방문하지 않은 링크에 스타일 적용하는 :link 가상 클래스 선택자
    - 웹 문서의 링크 중에서 사용자가 아직 방문하지 않은 링크에 스타일을 적용함. 텍스트 링크는 기본적으로 파란색 글자와 밑줄로 표시됨. 이때 링크의 밑줄을 없애거나 색상을 바꾸려면 :link 선택자를 사용함.

2. 방문한 링크에 스타일을 적용하는 :visited 가상 클래스 선택자
    - 웹 문서의 링크 중에서 한 번 이상 방문한 링크에 스타일을 적용함. 한번 이상 방문한 텍스트 링크는 보라색이 기본값임. 이때 사용자가 방문한 테긋트 링크와 색상이 달라지지 않게 하려면 :visited 선택자를 사용해 조절함.

3. 특정 요소에 마우스 포인터를 올려놓으면 스타일을 적용하는 :hover 가상 클래스 선택자
    - :hover 선택자는 웹 요소 위로 마우스 포인터를 올려놓을때 스타일을 적용함. 즉, 이 가상 클래스 선택자를 응용하면 이미지 위로 마우스 포인터를 올려놓았을 때 다른 이미지로 바뀌거나, 메인 메뉴 위로 마우스 포인터를 올려놓았을 때 서브 메뉴가 나타나는 효과

4. 웹 요소를 활성화했을 때 스타일을 적용하는 :active 가상 클래스 선택자 
    - :active 선택자는 웹 요소의 링크나 이미지 등을 활성화했을 때, 즉 클릭했을 때 스타일을 지정함, 예를 들어 어떤 웹 요소의 링크를 클릭하는 순간의 스타일을 지정할 수 있음.

5. 웹 요소에 초점이 맞추어졌을 때 스타일을 적용하는 :focus 가상 클래스 선택자
    - :focus 선택자는 웹 요소에 초점이 맞추어졌을 때 스타일을 적용함. 예를 들어 텍스트 필드 안에 마우스 포인터를 올려놓거나, 웹 문서에서 tab을 눌러 입력 커서를 이동했을 때 스타일을 지정함.

<br>
<br>

지금까지 설명한 1~4의 가상 클래스 선택자는 메뉴 링크에서 자주 사용하는데, 이때 다음과 같은 순서로 정의해야 함. 이 순서가 바뀌면 스타일을 정의하더라도 제대로 적용되지 않음.

1: link
2: visited
3: hover
4: active
```html
<style>
  .navi ul li{
    float: left;
    width: 150px;
    padding: 10px;
  }
  .navi a:link, .navi a:visited{ /* 방문한 링크와 방문하지 않은 링크 설정 */
    display: block;
    font-size: 14px;
    color: #000;
    padding: 10px;
    text-decoration: none; /* 밑줄을 없앰 */
    text-align:center;
  }
  .navi a:hover, navi a:focus{
    background-color: #222;
    color: #fff;
  }
  .navi a:active{
    background-color: #f00;
  }
</style>

  <nav class="navi">
    <ul>
      <li><a href="#">이용안내</a></li>
      <li><a href="#">1</a></li>
      <li><a href="#">2</a></li>
      <li><a href="#">3</a></li>
    </ul>
  </nav>
```

### 요소 상태에 따른 가상 클래스
웹 사이트나 애플리케이션 화면에서 요소의 상태에 따라 스타일을 적용할 수 있는데, 이때 가상 클래스 선택자를 사용함.

<br>

#### 앵커 대상에 스타일을 적용한 :target 가상 클래스 선택자
문서에서 같은 사이트나 다른 사이트의 페이지로 이동할 때에는 링크를 이용하고, 같은 문서안에서 다른 위치로 이동할때는 anchor를 이용함. 이때 target 선택자를 사용하면 앵커로 연결된 부분, 즉 앵커의 목적지가 되는 부분의 스타일을 쉽게 적용할 수 있음.
```html
<style>
  #intro:target{
    background-color: #0069e0;
    color: #fff;
  }
  </style>

  <nav class="navi">
    <ul>
      <li><a href="#intro">이용 안내</a></li>
      <li><a href="#room">객실 소개</a></li>
      <li><a href="#intro">예약 방법 및 요금</a></li>
      <li><a href="#ps-2.html">예약하기</a></li>
    </ul>
  </nav>
  <div id="intro" class="contents">
    <h2>이용 안내</h2>
  </div>
  <div id="room" class="contents">
    <h2>객실 소개</h2>
  </div>
  <div id="reservation" class="contents">
    <h2>예약 방법 및 요금</h2>
  </div>
```

### 요소의 사용 여부에 따라 스타일을 적용하는 ':enabled와 :disabled 가상 클래스 선택자'
해당 요소가 사용할 수 있는 상태일 때 스타일을 지정하려면 :enabled 선택자를 사용하고, 반대로 사용할 수 없는 상태일 때 스타일을 지정하려면 :disabled 선택자를 사용함. 예를 들어 textarea를 사용해 회원 약관을 보여 줄 때는 사용자가 입력할 수 없도록 disabled  속성을 지정해야 함. 이때 :disabled 선택자를 사용하면 텍스트 필드를 쉽게 적용할 수 있음.

### 선택한 항목의 스타일을 적용하는 :checked 가상 클래스 선택자
폼의 라이도 박스나 체크 박스에서 선택된 항목에는 checked라는 속성이 추가됨. 이렇게 checked 속성이 있는 요소의 스타일을 지정할 때 :checked 선택자를 사용하면 편리함

```html
<style>
  #signup input:checked + label{
    color:red;
    font-weight: bold;
  }
  </style>
  <ul>
    <li>
      <input type="radio" name="room" id="basic">
      <label for="basic">기본형(최대 2인)</label>
    </li>
    <li>
      <input type="radio" name="room" id="family">
      <label for="family">가족형(최대 8인)</label>
    </li>
  </ul>
```

### 구조 가상 클래스
웹 문서의 구조를 기준으로 특정 위치에 있는 요소를 찾아 스타일을 적용할 때 사용하는 가상 클래스 선택자임.

#### 특정 위치의 자식 요소 선택하기
 웹 문서에서 특정 요소에 스타일을 적용하려면 보통 class나 id 선택자를 사용해야 하는데, 지정할 요소가 몇 번째이니지를 따져 스타일을 적용할 수 있음.
 ```
 :only-child : 부모 안에 자식 요소가 하나뿐일 때 자식 요소를 선택함.
 A:only-type-of : 부모 안에 A 요소가 하나뿐일 때 선택함.
 :first-child : 부모 안에 있는 모든 요소 중에서 첫 번째 자식 요소를 선택함.
 :last-child : 부모 안에 있는 모든 요소 중에서 마지막 자식 요소를 선택함.
 A:first-of-type : 부모 안에 있는 A 요소 중에서 첫 번째 요소를 선택함.
 A:last-of-type : 부모 안에 있는 A 요소 중에서 마지막 요소를 선택함.
 :nth-child(n) : 부모 안에 있는 모든 요소 중에서 n번째 자식 요소를 선택함.
 :nth-last-child(n) : 부모 안에 있는 모든 요소 중에서 끝에서 n번째 자식 요소를 선택함.
 A:nth-of-type(n) : 부모 안에 있는 A 요소 중에서 n번째 요소를 선택함.
 A:nth-last-of-type(n) : 부모 안에 있는 A 요소 중에서 끝에서 n번째 요소를 선택함.
 ```
 ```html
 <style>
 .contents :nth-child(3){/*.contents의 세번째 자식 요소에 스타일 적용*/
  background-color : #ffff00;
 }
 .contents p:nth-of-type(3){ /*.contents의 p요소 중에서 세번째 자식 요소에 스타일 적용*/
  background-color : #00b900
 }
 </style>
 <div class="contents">
  <h2>이용 안내</h2>
  <p>Excepteur do.....</p>
  <p>Qui magna culpa.....</p> <!--contents의 모든 자식 요소 중에서 3번째이므로 1 스타일이 지정됨-->
  <h2>객실 소개</h2>
  <p>Irure incididunt...</p><!--contents의 p 자식 요소 중에서 3번째이므로 2번째 스타일임-->
  <h2>예약 방법 및 요금</h2>
 ```

 #### 수식을 사용해 위치 지정하기
 위치를 지정할때 1,3,5번째 처럼 위치가 계속 바뀌면 반복된 규칙을 찾아 an+b처럼 수식을 사용할 수 있음.
 ```css
 /*div 요소에서 세 번째 자식인 p 요소에 스타일 적용 */
 div p:nth-child(3)

/* div 요소에서 홀 수번째로 나타나는 자식인 p 요소에 스타일 적용 */
div p:nth-child(odd), div p:nth-child(2n+1)

/* div 요소에서 짝수 번째로 나타나는 자식인 p 요소에 스타일 적용 */
div p:nth-child(even), div p:nth-child(2n)
```
<br>

```css
table tr:nth-of-type(2n+1){ /*홀수 번째 열만 스타일 적용 */
  background: lightgray;
  color:black;
}
```
 
### 가상 요소
가상 클래스가 웹 문서의 여러 요소 중에서 원하는 요소를 선택한다면, 가상 요소는 문서 안의 특정 부분에 슽아리을 지정하기 위해 가상으로 요소를 만들어 추가함. 가상 요소를 만들어 사용하는 이유는 특별히 화면에 보이는 부분을 꾸밀 때 불필요한 태그를 사용하지 않도록 하기 위한 것임. 가상 요소는 가상 클래스와 구별하도록 가상 요소 앞에 콜론 2개(::)를 붙여서 표시함.

#### 첫 번째 줄, 첫 번째 글자에 스타일을 적용하는 ::first-line 요소, ::first-letter 요소
::first-line, first-letter 요소를 사용하면 지정한 요소의 첫 번째 줄, 첫 번째 글자에 스타일을 적용할 수 있음

#### 내용 앞뒤에 콘텐츠를 추가하는 ::before, ::after요소 
::before, ::after요소를 사용하면 지정한 요소의 내용 앞뒤에 스타일을 적용함
```html
<style>
  li.new::after{
    content: "NEW!";
    font-size:x-small;
    padding: 2px 4px;
    margin: 0 10px;
    border-radius: 2px;
    background: #f00;
    color: #fff;
  }
</style>
<div class="container">
  <h1> 제품 목록 </h1>
  <ul>
    <li class="new">제품 A</li>
    <li>제품 B</li>
    <li>제품 C</li>
    <li class="new">제품 D</li>
  </ul>
</div>
```

# 트렌지션 애니메이션

## transform과 변형 함수
CSS에서 변형을 적용하려면 transform 속성과 변형 함수 이름을 함께 작성해야 함.
```css
.photo {
  transform: translate(50px,100px);
}
```

### 2차원 변형과 3차원 변형
2차원 변형은 웹 요소를 평면에서 변형함. 예를 들어 수평 방향으로 이동하거나 수직 방향으로 왜곡함. 이렇게 평면에서변형할 때는 2차원 좌료플 사용하는데, x축은 오른쪽으로 갈수록 값이 커지고 y축은 아래로 내려갈수록 값이 커짐. 반면 3차원 변형은 x축과 Y축에 원금감을 주는 z축을 추가해서 변형함. 3차원 변형에서 z축은 앞뒤로 이동하며, 보는 사람 쪽으로 다가올수록 값이 커지고 뒤로 갈수록 값이 작아짐.
<img src="https://t1.daumcdn.net/cfile/tistory/202EA6484F0653932C">

### 2차원 변형 함수
```
translate(tx, ty) : 지정한 크기만큼 x축,y축으로 이동함
translateX(tx) : 지정한 크기만큼 x축으로 이동함
translateY(ty) : 지정한 크기만큼 y축으로 이동함
scale(sx, sy) : 지정한 크기만큼 x축과 y축으로 확대, 축소함
scaleX(sx) : 지정한 크기만큼 x축으로 확대, 축소함
scaleY(sy) : 지정한 크기만큼 y축으로 확대, 축소함
rotate(각도) : 지정한 각도만큼 회전함
skew(ax, ay) : 지정한 각도만큼 x축과 y축으로 왜곡함
skewX(ax) : 지정한 각도만큼 x축으로 왜곡함
skewY(ay) : 지정한 각도만큼 y축으로 왜곡함
```

### 3차원 변형 함수
2차원 변형 함수에 z축을 추가하면 3차원 변형함수가 됨.
```
translate3d(tx, ty, tz) : 지정한 크기만큼 x축, y축, z축으로 이동함
translateZ(tz) : 지정한 크기만큼 z축으로 이동함
scale3d(sx, sy, sz) : 지정한 크기만큼 x축과 y축, z축으로 확대, 축소함
scaleZ(sz) : 지정한 크기만큼 z축으로 확대, 축소함
rotate(rx, ry, 각도) : 지정한 각도만큼 회전함
rotate3d(rx, ry, rz, 각도) : 지정한 각도만큼 회전함
rotateX(각도) : 지정한 각도만큼 x축으로 회전함
rotateY(각도) : 지정한 각도만큼 y축으로 회전함
rotateZ(각도) : 지정한 각도만큼 z축으로 회전함
perspective(길이) : 입체적으로 보일 수 있도록 깊잇값을 지정함
```

### 웹 요소를 이동시키는 translate() 함수
translate() 함수는 x축이나 y축 또는 양쪽 방향으로 이동할 거리를 지정하면 해당 요소가 지정한 크기만큼 이동함.
```css
#movex:hover{
  transform: translateX(50px); /*x축으로 50px 이동*/
}
#movex:hover{
  transform: translate(10px, 20px); /* x축으로 10px, y축으로 20px 이동 */
}
```

### 요소를 확대, 축소하는 scale() 함수
scale() 함수는 웹 요소를 지정한 크기만큼 확대하거나 축소함.
```css
#sclaex {
  transform: scaleX(2); /*x축으로 2배 확대 */
}
#scale{
  transform:scale(0.7); /*x,y축으로 0.7배 확대
}
```

### 요소를 회전시키는 rotate()함수
요소를 회전시키는 rotate() 함수는 2차원 회전과 3차원 회전에서 모두 사용이 가능함.
```css
/*2차원 회전*/
#rotate1:hover{
  transform: rotate(40deg); /*오른쪽으로 40도 회전 */
}
#rotate2:hover{
  transform: rotate(-40deg); /*왼쪽으로 40도 회전 */
}
```
```css
/* perspective를 이용한 3차원 회전 */
.rotatex:hover{
  transform: rotateX(50deg); /* x축으로 50도 회전 */
}
#pers{
  perspective: 300px; /* 원근감 추가 */
}
```
```css
/* 3차원 회전 */
#rotatex:hover{
  transform: rotateX(55deg); /* x축으로 55도 회전 */
}
#rotatey:hover{
  transform: rotateY(55deg); /* y축으로 55도 회전 */
}
#rotatez:hover{
  transform: rotateZ(55deg); /* z축으로 55도 회전 */
}
#rotatexyz:hover{
  transform: rotate3d(2.5, 1.2, -1.5, 55deg); /* x,y,z축에 방향 벡터를 지정하고 있는 55도 회전 */
}
```

### 요소를 비틀어 왜곡하는 skew() 함수
지정한 각도만큼 요소를 비틀어 왜곡함. 이때 양쪽 방향으로 비틀거나 한쪽 방향으로만 비틀 수도 있음
```css
  #skewx:hover{
    transform: skewX(30deg); /*x축 기준으로 30도 비틀기 */
  }
  #skewy:hover{
    transform : skewY(15deg); /* y축 기준으로 15도 비틀기 */
  }
```

## 트랜지션 알아보기
하나의 스타일을 완전히 다른 스타일로 바꿈. 트랜지션에서는 스타일이 바뀌는 시간을 조절하여 자바스크립트를 사용하지 않고 애니메이션 효과를 낼 수 있음.

### 트랜지션과 속성
```
transition-property : 트랜지션의 대상을 지정함
transition-duration : 트랜지션을 실행할 시간을 지정함
transition-timing-function : 트랜지션의 실행 형태를 지정함
transition-delay : 트랜지션의 지연 시간을 지정함
transition : 위의 4가지 속성을 한꺼번에 정함
```
```css
transition-property: all;
transition-property: background-color;
transition-property: width, height;

transition-duration: 2s, 1s; /*트렌지션 시간 - 2초, 1초 */

transition: 2s ease-in; /*transition-property: 기본값 all / transition-duration: 2s / transition-timing-function : ease-in / transition-delay: 기본값 0 */
```

## 에니메이션 알아보기

### CSS 애니메이션에서 사용하는 속성
CSS3의 animation 속성은 특정 지점에서 스타일을 바꾸면서 애니메이션을 만드는데, 이렇게 애니메이션 중간에 스타일이 바뀌는 지점을 키프레임(keyframe)이라고 함. 키프레임은 @keyframes 속성으로 정의하고, animation 속성과 그 하위 속성을 이용해서 애니메이션의 실행 시간이나 반복 여부 등을 지정함.
```
@keyframes : 애니메이션이 바뀌는 지점을 지정함
animation-delay : 애니메이션의 시작 시간을 지정함
animation-direction : 애니메이션을 종료한 뒤 처음부터 시작할지, 역방향으로 진행할지 지정함
animation-duration : 애니메이션의 실행 시간을 지정함
animation-iteration-count : 애니메이션의 반복 횟수를 지정함
animation-name : @keyframes로 설정해 놓은 중간 상태를 지정함
animation-timing-function : 키프레임의 전환 형태를 지정함
animation : animation 속성을 한꺼번에 묶어서 지정함
```
```css
@keyframes shape{
  from{
    border: 1px solid transparent; /* 1px짜리 투명 테두리에서 */
  }
  to{
    border: 1px solid #000; /* 검은색 테두리로 변경 */
    border-radius: 50%; /* 테두리를 둥글게 변경 */
  }
}
@keyframes rotate{
  from{
    transform: rotate(0deg); /* 0도에서 시작해서 */
  }
  to{
    transform: rotate(45deg); /* 45도까지 회전하기 */
  }
}

#box1{
  background-color: #4cff00;
  border: 1px solid transparent;
  animation-name: shpae;
  animation-duration: 3s;
  animation-iteration-count: infinite;
}
```


# 반응형 웹과 미디어 쿼리
반응형 웹 디자인 PC 브라우저이든 모바일 브라우저이든 사용자의 접속 환경에 맞추어 사이트의 레이아웃을 자연스럽게 바꾸어 보여 주는 것을 말함. 

<br>
<br>

## 반응형 웹 알아보기
화면 크기가 다양한 모바일이 계속 쏟아져 나오는데 그때마다 사이트를 따로 제작하는 것은 매우 비효율적임. 이런 점을 고려해 화면 크기에 '반응'하는 화면 요소를 자동으로 바꾸어 사이트를 구현하는 것을 반응형 웹 디자인 이라고 함. 

<br>
<br>

### 모바일 기기를 위한 뷰포트
PC에 맞게 제작한 웹 사이트를 모바일 기기에서 접속해서 보면 모든 내용이 자게 표시됨. 그 이유는 PC 화면과 모바일 화면에서 표시되는 픽셀의 차이 때문인데, 뷰포트를 지정하면 접속한 기기의 화면에 맞추어 확대하거나 축소해서 표시할 수 있음. 이때 '뷰표트'는 스마트폰 화면에서 실제 내용이 표시되는 영역임. 
```
예를 들어 웹 페이지 너비를 스마트폰용인 320px로 맞추어 웹 사이트를 제작하더라도 스마트폰용 모바일 브라우저의 기본 뷰포트 너비가 980spx이므로 웹 페이지 너비를 무조건 980px로 표시하려고 함. 결국 스마트폰용으로 제작한 웹 페이지의 내용은 의도와 달리 작은 글씨와 그림으로 표시가 됨.
```
```
웹 키트를 기반으로 한 브라우저란 브라우저를 동작시키는 실행 엔진이 '웹키트 엔진'이라서 붙은 이름임. 크롬, 엣지 등을 비롯해 대부분의 브라우저는 웹 키트 엔진을 기반으로 함.
```
![img](https://blog.kakaocdn.net/dn/epEyg0/btqHuid1BFM/MKkgfZ5hacAry7zUkdp3s1/img.png)


### 뷰포트 지정하기
뷰포트는 `<meta>`태그를 이용해 `<head></head>` 태그 사이에 작성함. 
```
<meta name="viewport" content="속성1=값1", "속성2=값2", ...">
```
<h3>뷰포트의 속성</h3>

```
|  종류   |         설명          |                     사용 가능한 값                 |             기본값                 |
width : 뷰포트 너비                       device-width  또는 크기                  브라우저 기본값
height : 뷰포트 높이                     device-height 또는 크기                   브라우저 기본값
user-scalale: 확대 축소 가능 여부           yes 또는 no                                      yes
initial-scale : 초기 확대, 축소 값                1 ~ 10                                              1
```



뷰포트 속성으로 웹 페이지 뷰포트의 너비를 스마트폰 화면 너비에 맞추고 초기 화면 배율을 1로 지정함
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### 뷰포트 단위
뷰포트 개념이 등장하기 전까지는 CSS에서 크기를 지정할 때 주로 Px, %의 단위를 사용했지만 이제는 다음과 같이 뷰포트를 기준으로 하는 단위를 사용할 수 있음.

```
vw : 1vw는 뷰포트 너비의 1%와 같음
vh : 1vh는 뷰포트 높이의 1%와 같음
vmin : 뷰포트의 너비와 높이 중에서 작은 값의 1%와 같음
vmax : 뷰포트의 너비와 높이 중에서 큰 값의 1%와 같음
```
예를 들어 뷰포트의 너비가 1000px, 높이가 800px일 경우 1vw는 10px, 1vh는 8px임. 1vmin은 너빗값과 높잇값 중 작은 값인 800px의 1%인 8px이 됨. 그렇다면 vmax는 10px이 됨. 만약 화면을 돌린다면 방향이 바뀌므로 1vw는 8px, 1vh는 10px이 됨. 하지만 작은 값과 큰 값의 변화가 없으므로 vmin은 8px, vmax는 10px이 그대로 유지됨.

```css
h1{
  font-size : 5vw;
  text-align : center;
}
```
![img](https://blog.kakaocdn.net/dn/bFiJvN/btqGUctnSKA/46YlyE00GFUay2MYNKLci0/img.png)

<br>
<br>

## 미디어 쿼리 알아보기
미디어 쿼리는 반응형 웹 디자인에서 가장 기본적인 개념, 사이트에 접근하는 기기의 해상도에 따라 서로 다른 스타일 시트를 적용해 줌. 미디어 쿼리가 무엇인지 알아보고, 미디어 쿼리를 사용할 떄 고려해야 할 조건도 있음.
CSS는 모듈인 미디어 쿼리는 사이트에 접속하는 장치에 따라 특정한 CSS 스타일을 사용하는 방법임. 미디어 쿼리를 사용하면 접속하는 기기의 화면 크기에 따라 에이아웃이 달라짐.

<br>

### 미디어 쿼리 구문
미디어 쿼리는 @media 속성을 사용해 특정 미디에서 어떤 CSS를 적용할 것인지 지정해 줌. 
```css
@media screen and (min-width : 768px) and (max-width : 1439px){
}
```

#### 미디어 유형의 종류
```
all : 모든 미디어 유형에서 사용할 css를 정의함
print : 인쇄 장치에서 사용할 css를 정의함
screen : 컴퓨터 스크린에 사용할 css를 정의함.  스마트폰 스크린도 포함됨
tv : 음성과 영상이 동시 출력되는 tv에서 사용할 css를 정의함
aural : 음성 합성 장치에서 사용할 css를 정의함
braille : 점자 표시 장치에서 사용할 css를 정의함
handheld : 패드처럼 손에 들고 다니는 장치를 위한 css를 정의함
projection : 프로젝터를 위한 css를 정의함
tty : 디스플레이 기능이 제한된 장치에 맞는 css를 정의함. 이런 장치에서는 픽셀 단위를 사용할 수 없음.
embossed : 점자 프린터에서 사용할 css를 정의함


@media screen {

}
@media print{

}
```

<br>

#### 웹 문서의 가로 너비와 세로 높이 속성
실제 웹 문서 내용이 화면에 나타나는 영역을 뷰포트라고 하는데 뷰포트의 너비와 높이를 미디어의 쿼리의 조건으로 사용할 수 있음. 

```
width, height : 웹 페이지의 가로 너비, 세로 높이를 지정함
min-width, min-height : 웹 페이지의 최소 너비, 최소 높이를 지정함
max-width, max-height : 웹 페이지의 최대 너비, 최대 높이를 지정함
```
```css
@media screen and (min-width : 1440px){

}
```

#### 단말기의 가로 너비와 세로 높이 속성
단말기에서 기본으로 제공하는 물리적인 가로 너비와 세로 높이가 있는데 단말기의 너비와 높이는 단말기 브라우저 창의 너비와 높이를 말함. 이때 주의할 점은 대부분의 단말기 해상도와 실제 브라우저의 너비가 다르다는 것임. 

```
device-width, device-height : 단말기의 가로 너비, 세로 높이를 지정함
min-device-width, min-device-height : 단말기의 최소 너비, 최소 높이를 지정함
max-device-width, max-device-height : 단말기의 최대 너비, 최대 높이를 지정함
```

#### 화면 회전 속성
미디어 쿼리에서 orientation 속성을 사용하면 기기의 방향을 확인할 수 있고, 그에 따라서 웹 사이트의 레이아웃을 바꿀 수 있음. orientation 속성값으로는 portrait와 landscape가 있음. 가로 모드는 landscape이고 세로 모드는 portrait이며 기본값은 landscape임.

```
orientation: protrait : 단말기의 세로 모드를 지정함
orientation: landscap : 단말기의 가로 모드를 지정함
```
```css
@media screen and (min-device-width: 812px) and (orientation: landscape){

}
```

#### 미디어 쿼리의 중단점
미디어 쿼리를 작성할 때 화면 크기에 따라 서로 다른 css를 적용할 분기점을 중단점이라고 함. 이 중단점을 어떻게 지정하느냐에 따라 css가 다라지고 화면 레이아웃이 바뀌는데, 대부분 기기의 화면 크기를 기준으로 함. 하지만 시중에 나온 모든 기기를 반영할 수는 없으므로 모바일과 태블릿, 데스크톱만 구분하는 것이 좋음.<p>
그리고 처리 속도나 화면 크기 등에서 다른 기기보다 모바일의 제약 조건이 더 많으므로 모바일의 레이아웃을 기본으로 하여 CSS를 만듬. 그러고 나서 사양이 좀 더 좋고 화면이 큰 태블릿과 데스크톱에 맞춰 더 많은 기능과 스타일을 추가함. 이렇게 모바일을 먼저 고려하여 미디어 쿼리를 작성하는 것을 모바일 퍼스트 기법이라고 함.
```
디자이너에 따라 데스크톱을 기준으로 디자인한 뒤 모바일에 맞춰 기능을 줄이고 스타일을 바꿔 가는 방법을 선택하기도 함
```
- 스마트폰 : 모바일 페이지는 미디어 쿼리를 사용하지 않고 기본 CSS로 작성함. 만일 스마트폰의 방향까지 고려해서 제작한다면 min-width의 세로와 가로를 각각 portrait 320px, landscape 480px로 지정함
- 태블릿 : 세로 크기가 768px 이상이면 태블릿으로 지정함. 가로 크기는 데스크톱과 똑같이 1024px이상으로 지정함
- 데스크톱 : 화면 크기가 1024px 이상이면 데스크톱으로 설정함
(모바일 기기의 뷰포트 크기는 yesviz.com/devices.php)

<br>

### 미디어 쿼리 적용하기
미디어 쿼리는 크게 외부 CSS 파일로 연결하는 방법과 웹 문서에 직접 정의하는 방법이 있음

####  - 외부 CSS 파일 연결하기
외부 CSS 파일을 따로 저장해서 만드는 방법이 있는데 ```<link>``` 태그나 ```@import```문을 사용함.
```html
<link rel = "stylesheet" media="print" href="css/print.css">

<style>
  @import url("css/tablet.css") only screen and (min-width: 321px) and (max-widyh: 769px);
</style>
```
```
<link>태그와 @import문
<link>태그와 @import문은 모두 외부에서 CSS파일을 가져와 사용하는 방법임. CSS파일이 한두개밖에 없다면 속도나 처리면 에서는 큰 차이가 없음. 하지만 익스플로어의 @경우 import문과 자바스크립트가 함께 있을 때 자바스크립트를 먼저 내려받은 후에 @import문에 있는 CSS를 다운받음. 그래서 자바스크립트에서 스타일과 관련된 정보를 처리해야 할 경우 오류가 날 수도 있음. 그래서 CSS 파일이 많고 규모가 큰 사이트를 개발한다면 @import문보다 <link>를 주로 사용함.
```

#### 웹 문서에 직접 정의하기
외부 CSS파일을 만들지 않고 웹 문서에서 미디어 쿼리를 직접 지정하는 방법 이 있는데 첫 번째는 ```<style>``` 태그 안에서 media속성을 사용하여 조건을 지정하고, 그 조건에 맞는 스타일 규칙을 정의하는 것
```html
<style media = "screen and (max-width: 320px)"> /*너비가 320px 이하일 때 배경색을 주황색) */
  body{
    background-color : orange;
  }
</style>
```

두번째는 스타일을 선언할 때 @media 문을 사용해 각 조건별로 스타일을 지정해 놓고 스타일을 선택해서 적용하는 것
```html
<style>
  @media screen and (max-width: 320px){
    body{
      background-color : orange;
    }
  }
</style>
```

## 그리드 레이아웃
웹 사이트의 레이아웃을 정할 때 사이트 전체 디자인이나 일관성을 유지하려면 그리드 레이아웃을 사용해야 함. 반응형 웹 디자인을 사용한 사이트는 화면 너비에 따라 웹 문서의 요소를 재배치해야 함. 이때 기준 레이아웃이 필요한대 이때 그리드 레이아웃을 사용함. 그리드 레이아웃이란 웹 사이트를 여러 개의 칼럼으로 나눈 후 메뉴나 본문, 이미지 등의 웹 요소를 화면에 맞게 배치하는 것을 말함.<p>
그리드 레이아웃이란 웹 사이트를 여러 개의 칼럼으로 나눈 후 메뉴나 본문, 이미지 등의 웹 요소를 화면에 맞게 배치하는 것을 말함. 그리드 레이아웃을 사용하면 화면을 규칙적으로 배열하므로 레이아웃을 일관성 있게 유지할 수 있음.
-  시각적으로 안정된 디자인을 만들 수 있음.
- 업데이트가 편한 웹 디자인을 구성할 수 있음.
- 요소를 자유롭게 배치할 수 있음.

<br>

### 그리드 레이아웃 만들기
반응형 웹 디자인에 적합한 그리드 레이아웃을 만드는 방법은 여러 가지가 있음. 기존 가변 그리드를 css의 float 속성으로 사용할 수도 있고, 플렉서블 박스 레이아웃이나 css 그리드 레이아웃으로 적용할 수도 있음.

<br>

#### 플렉서블 박스 레이아웃
플렉서블 박스 레이아웃은 그리드 레이아웃을 기본으로 하고 각 박스를 원하는 위치에 따라 배치하는 것임. 이때 여유 공간이 생길 경우 너비나 높이를 적절하게 늘이거나 줄일 수도 있음. 플렉서블 박스 레이아웃은 흔히 플렉스 박스 레이아웃이라고도 하므로 앞으로는 줄여서 플렉스 박스라고 함.<p>
플렉스 박스는 수평 방향이나 수직 방향 중에서 한쪽을 주축으로 정하고 박스를 배치함. 박스를 왼쪽에서 오른쪽으로 순서대로 배치하는데, 화면 너비를 넘어가면 수직으로 이동해서 다시 순서대로 배치가됨.

![flexbox](https://t1.daumcdn.net/cfile/tistory/2454A93D568784B40D)

#### CSS 그리드 레이아웃
그리드 레이아웃을 많이 사용하면서 플렉스 박스에 이어 CSS 그리드 레이아웃이라는 새로운 CSS 표준이 만들어짐. 플렉스 박스를 사용할 때는 '주축'이라는 개념이 있어서 수평이나 수직 중 하나를 기준으로 해서 요소를 배치함. 하지만 CSS 그리드 레이아웃은 수평과 수직 어느 방향이든 배치할 수 있음. 마치 레고 블록을 끼워 맞추듯 요소를 배치한다고 생각하면 되고, 대부분 모던 브라우저에서 사용할 수 있음.

## 플렉스 박스 레이아웃 
플렉스 박스 레이아웃은 비교적 최근 등장한 개념이고 그리드 레이아웃을 기본으로 함.
![flexboxlayout](https://velog.velcdn.com/images%2Fhanan0105%2Fpost%2F8a2016e2-d133-4209-bffa-4ae939271da2%2Fimage.png)

<br>

### 플렉스 박스 항목을 배치하는 속성
플렉스 박스에는 플렉스 항목이 여러 개 있는데 일괄적으로 한꺼번에 배치할 수도 있고, 주축이나 교차축 기준으로 다양하게 배치할 수도 있음.
```
justify-content : 주축 방향의 정렬 방법
align-items : 교차축 방향의 정렬 방법
align-self : 교차축에 있는 개별 항목의 정렬 방법
align-content : 교차축에서 여러 줄로 표시된 항목의 정렬 방법
```

#### 플렉스 컨테이너를 지정하는 display 속성
플렉스 박스 레이아웃을 만들려면 먼저 웹 콘텐츠를 플렉스 컨테이너로 묶어 주어야함. 즉, 배치할 웹 요소가 있다면 그 요소를 감싸는 부모 요소를 만들고, 그 부모 요소를 플렉스 컨테이너로 만들어야 함. 이때 플렉스 컨테이너로 동작하려면 display 속성을 이용해 이 부분을 플렉스 박스 레이아웃을 적용하겠다고 지정해야 함.
```
flex : 컨테이너 안의 플렉스 항목을 볼록 레벨 요소로 배치함
inline-flex : 컨테이너 안의 플렉스 항목을 인라인 레벨 요소로 배치함
```

#### 플렉스 방향을 지정하는 flex-directon 속성
플렉스 컨테이너 안에서 플렉스 항목을 배치하는 주축과 방향을 지정하는 속성임.
```
row : 주축을 가로로 지정하고 왼쪽에서 오른쪽으로 배치
row-reverse : 주축을 가로로 지정하고 반대로 오른쪽에서 왼쪽으로 배치
column : 주축을 세로로 지정하고 위쪽에서 아래쪽으로 배치
column-reverse : 주축을 세로로 지정하고 아래쪽에서 위쪽으로 배치
```
ex) 다음은 1, 2, 3이라는 숫자가 써 있는 박스 3개를 플렉스 컨테이너로 묶고, 컨테이너 안에 있는 플렉스 항목을 여러 방법으로 배치한 것임.
```css
  .container {
    display: flex; /*플렉스 컨테이너 지정*/
  }
  #opt1{
    flex-direction: row; /*왼쪽에서 오른쪽으로*/
  }
  #opt2{
    flex-direction: row-reverse; /*오른쪽에서 왼쪽으로*/
  }
  #opt3{
    flex-direction: column; /*위에서 아래로*/
  }
  #opt4{
    flex-direction: column-reverse; /*아래에서 위로*/
  }
```


#### 플렉스 항목의 줄을 바꾸는 flex-wrap 속성
flex-wrap 속성은 플렉스 컨테이너 너비보다 많은 플렉스 항목이 있을 경우 줄을 바꿀지 여부를 지정함. 속성값으로 wrap이나 wrap-reverse로 지정한 후 웹 브라우저 화면의 너비를 늘리거나 줄여 보면 ㅡㄹ렉스 컨테이너 너비에 따라 여러줄로 표시됨.
```
nowrap : 플렉스 항목을 한줄에 표시함(기본값)
wrap : 플렉스 항목을 여러 줄에 표시함
wrap-reverse : 플렉스 항목을 여러 줄에 표시하되, 시작점과 끝점이 바뀜
```
```css
#opt1{
  flex-wrap : nowrap;/*한 줄에 표시*/
}
#opt2{
  flex-wrap : wrap; /*여러 줄에 표시*/
}
#opt3{
  flex-wrap : wrap-reverse; /*항목의 순서를 바꿔 여러 줄에 표시*/
}
```

#### 배치 방향과 줄 바꿈을 한꺼번에 지정하는 flex-flow 속성
flex-flow속성은 flex-direction 속성과 flex-wrap 속성을 한꺼번에 지정하여 플렉스 항목의 배치 방향을 결정하거나 줄을 바꿈
```css
#opt1{
  flex-flow: row wrap; /*왼쪽에서 오른쪽, 여러 줄*/
}
#opt2{
  flex-flow: row nowrap; /*왼쪽에서 오른쪽, 한 줄*/
}
```

#### 주축 정렬 방법을 지정하는 justify-content 속성
justify-content 속성은 주축에서 플렉스 항목 간의 정렬 방법을 지정함
```
flex-start : 주축의 시작점에 맞춰 배치함
flex-end : 주축의 끝점에 맞춰 배치함
center : 주축의 중앙에 맞춰 배치함
space-between : 첫 번째 항목과 끝 항목을 주축의 시작점과 끝점에 배치한 후 나머지 항목은 그 사이에 같은 간격으로 배치함
space-around : 모든 항목을 주축에 같은 간격으로 배치함
```
```css
#opt1{
  justify-content: flex-start; /*주축 시작점 기준 */
}
#opt2{
  justify-content: flex-end; /*주축 끝점 기준 */
}
#opt3{
  justify-content: center; /*주축 중앙 기준 */
}
#opt4{
  justify-content: space-between; /* 시작점과 끝점 배치한 후 같은 간격 */
}
#opt5{
  justify-content: space-around; /*전체 항목 같은 간격 */
}
```

#### 교차축 정렬 방법을 지정하는 align-items 속성
justify-content 속성이 주축에서 항목을 정렬하는 방법이라면, align-items 속성은 교차축을 기준으로 플렉스 항목을 정렬함
```
flex-start : 교차축의 시작점에 맞춰 배치함
flex-end : 교차축의 끝점에 맞춰 배치함 
center : 교차축의 중앙에 배치함
baseline : 교차축의 문자 기준선에 맞춰 배치함
stretch : 플렉스 항목을 늘려 교차축에 가득 차게 배치함
```
```css
#opt1{
  align-items: flex-start; /*주축 시작점 기준으로 배치*/
}
#opt1{
  align-items: flex-end; /*주축 끝점 기준으로 배치*/
}
#opt1{
  align-items: center; /* 주축 중앙 기준으로 배치 */
}
#opt1{
  align-items: baseline; /* 문자 기준선에 맞춰 배치*/
}
#opt5{
  align-items: stretch; /* 항목을 늘려 교차축에 가득 차게 배치 */
}
```

#### 특정 항목만 정렬 방법을 지정하는 align-self속성
align-item 속성은 교차축을 기준으로 플렉스 항목의 정렬 방법을 결정하지만 그중에서 특정 항목만 지정하고 싶다면 align-self 속성을 사용함. 그래서 align-item 속성은 플렉스 컨테이너를 지정하는 선택자에서 사용하지만 align-self 속성은 플렉스 항목 선택자에서 사용함. align-self속성에서 사용하는 값은 align-items 속성에서 사용하는 값과 같음.
```css
.container{
  display: flex; /*플렉스 컨테이너 지정 */
  align-items: center; /*교차축의 중앙에 배치 */
}
#box1{
  align-self: flex-start; /* 교차축의 시작점에 배치 */
}
#box3{
  align-self: stretch; /* 교차축에 가득차게 늘림 */
}
```

#### 여러 줄일 때 교차축 정렬 방법을 지정하는 align-content속성
주축에서 줄 바꿈이 생겨서 플렉스 항목을 여러 줄로 표시할 때 align-content 속성을 사용하면 교차축에서 플렉스 항목 간의 간격을 지정할 수 있음.
``` 
한 줄일 경우에는 align-items 속성을 사용

flex-start : 교차축의 시작점에 맞춰 배치
flex-end : 교차축의 끝점에 맞춰 배치
center : 교차축의 중앙에 맞춰 배치
space-between : 첫 번째 항목과 끝 항목을 교차축의 시작점과 끝점에 맞추고 나머지 항목은 그 사이에 같은 간격으로 배치함
space-around : 모든 항목을 교차축에 같은 간격으로 배치
stretch : 플렉스 항목을 늘려서 교차축에 가득 차게 배치
```

```css
.container{
  display : flex;
  flex-flow : row wrap;
}
#opt1{ align-content : flex-start; } /* 교차축 시작점 기준 */
#opt2{ align-content : flex-end; } /* 교차축 끝점 기준 */
#opt3{ align-content : center; } /* 교차축 중앙 기준 */
#opt4{ align-content : space-between; } /* 시작점과 끝점에 배치한 뒤 중간 항목은 같은 간격으로 배치 */
#opt5{ align-content : space-around; } /* 전체 항목을 같은 간격으로 배치 */
#opt6{ align-content : stretch; } /* 항목을 늘려 교차축에 가득 차게 배치 */
```

#### 플렉스 레이아웃을 활용해 항상 중앙에 표시하기
플렉스 박스 레이아웃을 사용하면 화면 요소를 세로 방향으로 중앙에 배치하는 것이 간단해짐.
```css
*{
  margin: 0;
  box-sizing: border-box;
}
body{
  background : url('') no-repeat left top fixed;
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
button{

}
```

## CSS 그리드 레이아웃 
웹 디자인 레이아웃을 만들 때 그리드 레이아웃은 아주 중요함. 웹 사이트를 제작할 때 고려해야 할 기기가 나날이 늘어나고 있기 때문인데, 소스를 최대한 간단하게 유지하면서 대부분의 기기에 대응할 수 있는 그리드 레이앙수 기법이 바로 CSS 그리드 레이아웃임. 플렉스 박스 레이아웃은 플렉스 항목을 배치할 때 가로나 세로 중에서 하나를 주축으로 정해 놓고 배치하지만 CSS 그리드 레이아웃에서는 그리드 항목을 배치할 때 가로와 세로를 모두 사용함. 그래서 플렉스 항목은 1차원이고 CSS 그리드 레이아웃은 2차원이라고 말함
![gridlayout](https://968663149-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LH1dN99ZXtZTFG_0JKV%2F-LH5dU3TZ9KBFb0v9kxv%2F-LH5fZWVTqFDi6AV1QNB%2Fimage.png?alt=media&token=9890257b-f37b-45a5-97ef-8f92820ca82e)

<br>
<br>

### CSS 그리드 레이아웃 항목을 배치하는 속성
CSS 그리드 레이아웃은 가장 최근에 제안된 그리드 레이아웃 제작 방법임

<br>

#### 그리드 컨테이너를 지정하는 display 속성
그리드 레이아웃을 지정할 때에는 가장 먼저 그리드를 적용할 요소의 바깥 부분을 그리드 컨테이너로 만들어야 함. 그리드 컨테이너를 만들 때는 display 속성을 grid나 inline-grid로 지정함
```
grid : 컨테이너 안의 항목을 볼록 레벨 요소로 배치
inline-grid : 컨테이너 안의 항목을 인라인 레벨 요소로 배치
```

<br>

#### 칼럼과 줄을 지정하는 grid-template-columns, grid-template-rows 속성
그리드 컨테이너 안에 항목을 배치할 때 칼럼과 줄의 크기와 개수를 지정하려면 grid-template-columns 속성과 grid-template-rows 속성을 각각 사용함. grid-template-columns 속성은 그리드 컨테이너 안의 항목을 몇 개의 칼럼으로 배치할지, 각 칼럼의 너비를 얼마로 할지 지정함.
```css
#wrapper{
  display: grid; /*그리드 컨테이너 지정 */
  grid-template-columns : 200px 200px 200px; /* 너비가 200px인 칼럼 3개 */
  grid-template-rows : 100px; /* 줄 높이 100px */
}
```

#### 상대적인 크기를 지정하는 fr 단위
그리드 레이아웃에서 컬럼이나 줄의 크기를 지정할 때 픽셀(px)을 이용하면 항상 크기가 고정되므로 반응형 웹 디자인에는 적합하지 않음. 그래서 그리드 레이아웃에서는 상대적인 크기를 지정할 수 있도록 fr(fraction) 단위를 사용함.
```css
grid-template-columns: 1fr 1fr 1fr; /*너비가 같은 칼럼 3개 */

grid-template-columns: 2fr 1fr 2fr; /* 칼럼을 2: 1: 2로 배치 */
```

#### 값이 반복될 때 줄여서 표현할 수 있는 repeat() 함수
px이나 fr단위를 사용하면 똑같은 값을 여러 번 반복해야 함. CSS 그리드 레이아웃에는 내장된 repeat() 이라는 함수를 사용하면 반복하지 않고 간단하게 표헌할 수 있음
```css
gride-template-columns : 1fr 1fr 1fr;
 /*같은 표현식 */
grid-template-columns : repeat(3,1fr);
```

#### 최솟값과 최댓값을 지정하는 minmax() 함수
줄 높이보다 내용이 더많으면 보이지가 않는데, minmax() 함수를 사용하면 줄 높이를 고정하지 않고 최솟값과 최댓값을 사용해서 유연하게 지정이 가능함
```css
#wrapper{
  width: 600px;
  display: grid; /*그리드 컨테이너 지정 */
  grid-template-columns: repeat(3, 1fr); /*너비가 같은 칼럼 3개*/
  grid-template-rows: minmax(100px, auto); /*줄 높이는 최소 100px*/
}
```

#### 자동으로 칼럼 개수를 조절하는 auto-fill, auto-fit값
repeat()를 사용해 크기가 같은 칼럼을 반복할 때는 칼럼의 개수를 지정하는데, 이때 칼럼의 너빗값과 함께 auto-fit이나 auto-fill을 지정하면 화면 너비에 따라 칼럼 개수를 조절할 수 있음. 
```css
grid-template-columns : repeat(auto-fit, 200px);
```
auto-fit이나 auto-fill 모두 칼럼 개수를 자동으로 조절해 주므로 화면이 넓어지면 칼럼 개수가 많아지고 반대로 화면이 좁아지면 칼럼 개수가 줄어듬. 두 값의 차이는 남는 공간을 채울지 말지 여부에 있음.
```css
#wrapper1{
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  margin-bottom: 20px;
}
#wrapper2{
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
}
```
![auto](https://velog.velcdn.com/images%2Fdongha1992%2Fpost%2F0c6c3f10-7a3f-4bde-aa8d-453fea787c58%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-09-09%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.51.46.png)

#### 그리드 항목의 간격을 지정하는 grid-column-gap, grid-row-gap, grid-gap 속성
그리드 레이아웃은 기본적으로 항목들이 서로 붙어 있음. 이때 조절하는 함수를 사용하면 조절이 가능함
```
grid-column-gap: 칼럼과 칼럼 사이의 간격을 지정함
grid-row-gap: 줄과 줄 사이의 간격을 지정함
grid-gap : 칼럼과 줄 사이의 간격을 한꺼번에 지정함
```
```css
#wrapper{
  display: grid;
  grid-template-columns: repeat(3, 200px);
  grid-gap: 20px 30px; /*칼럼 간격 30px, 줄 간격 20px */
}
```

#### 그리드 라인을 이용해 배치하기
그리드 레이아웃은 눈에 보이지 않는 그리드 라인이 포함되어 있음. 예를 들어 칼럼 3개와 줄 3개로 이루어진 그리드 레이아웃이 있을때, 칼럼라인은 앞에서부터 번호가 매겨지므로 총 4개임. 마찬가지로 줄에서도 총 4개의 줄 라인이 있음 또한 그리드 라인 속성을 이용해서 그리드 항목을 배치할 수 있음
![gridline](https://968663149-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LH1dN99ZXtZTFG_0JKV%2F-LH5dU3TZ9KBFb0v9kxv%2F-LH5fxvo4g7OuwZzrtOr%2Fimage.png?alt=media&token=e5e56b1f-069d-4afa-85b7-1e09c35464ac)


```
grid-column-start : 칼럼 시작의 라인 번호를 지정함 | grid-column-start: 1
grid-column-end : 칼럼 시작의 라인 번호를 지정함 | grid-column-end: 1
grid-column : 칼럼 시작의 라인 번호를 지정함 | grid-column: 1/4
grid-row-start : 칼럼 시작의 라인 번호를 지정함 | grid-end-start: 2
grid-row-end : 칼럼 시작의 라인 번호를 지정함 | grid-row-end: 4
grid-row : 칼럼 시작의 라인 번호를 지정함 | grid-row: 2/4
```
```css
#wrapper{
  width: 700px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 100px);
}
```

```css
.box1{
  background-color: 3689ff;
  grid-column: 1/4;
}
.box2{
  background-color: #00cf12;
  grid-row: 2/4;
}
.box3{
  background-color: #ff9019;
  grid-column: 2/4;
  grid-row-start: 2;
}
.box4{
  background-color: #ffd000;
  grid-column-start: 3;
  grid-row-start: 3;
}
```
![gridlayoutex](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAU0AAACXCAMAAACm/PkLAAABdFBMVEU2if////8AzxL/kBn/0ACoxv8ohP8qif+WjMD/kAD/zAAAywA3h///kyQA0gD/kRn/1AAopb/I8Mn/iAD/6dvN3f//9doegf/d6P//ixr/jAD///U6g/87gP9kvP//9f//vK7l7f/t8/8LfP+05//N0/9osf+t4v/EzP+Uyv/a8f/3/v/r6P9+sv/n+P+Xrf/c2f8Acf/o//+ct/9CeP+AyP89ov/17P+Duv+Fpf+74v9wnP//9/+8wv/g4f9asf/L5OsU0mzt/N1U1QBY45697bqL3kz/88b/ya7/1q75/+e47qaG4qL/fwD/oX3/0qH/2tpi0iEA0kDR+O2m5GOC68je8Zoa1Wb/rXv/8+//tjn/xnj/ogD/pWHn9reu9/bL6YN21AAt2Yr/1oX/riD/1cD/5+u35FAAz1D/oI3m+umu5W1f1zb/y4D/tpj/s2T/1lf/4nP//9X/5Zz/6q7/2Dz/5Yb/7pn/5C//6sb/4lf/64/3icSzAAADq0lEQVR4nO3b/1MTRwCG8WxNr5JLwJrI0buWClQRA2pjhbZarcaSNiqKgBhBkdZGSlsEkiDUf765Th058cuEe3MJ8Xkmk8zNZGdvPtmb3V8SM6Qr1uob6KjQVIamMjSVoakMTWW+5sDHFKbBgOaxIYv231BfUNOJ0f5z0BSGpjI0laGpDE1lB0TTsnZfJa23fa/FHQxN56sTuwCdkyc+b929vKsDojl8asiJWY5jOfUj8oj58otW39GbOyiap7OjyRFjxs6cHRm1+tEMkzN87uvcefPNhYnx7EQSzXA5wxPfZr/Ljn0/2j8weNHpv4RmiKyRY30/OGMDl8f7Ll44Z125zC4UJn8DiiUdJ+kk64clTkgfRGgqQ1MZmsrQVIamMjSVoakMTWVoKkNTGZrK0FSGpjI0laGpDE1laCpDUxmaytBUhqYyNJWhqQxNZWgqQ1PZHs1kVH3Sgb2m+eOnkXW4Ewv+z/Jod2S5XZ1XOhPUtD+Kqs8OdV5oKkNTGZrK0FSGprIwmt2BL9t2Y79E8zXddODKbfqEYTS7r17L78K8/tNkQ5xN13SPF3Zxpn7+JdXsGcNpFvO2vyT9VWlfvXHT5N8/KFLNzVvp+gJNu2nXTU/dvlPoavaU4TSPFqfvznizc/fuzkza822n2Vvace+XSg/KC1OZxYd3bjf9WQ+l6U3PPVp6PJ9dXlqdtH81s+32pBfT5d8uLUyZVNl7kvq9XG3vtenl65pPV3LLS97yfG66zXahuuatuuaTKdNVLi4+7Pqj2NPsKUNprq56+ZWc+XPu3srqzVzW/NVemmsZ0+veN96D8t9rmWfGe9bOT3r9hGS/3IX+34vaStPfgF7tQv5n02fk9K4MTWVoKkNTGZrK0FSGpjI0laGpDE1laCpDUxmaytBUhqYyNJWhqQxNZWgqQ1MZmsrQVIamMjSVoakMTWVoKkNTWes0U9HVE1Ut07RNdMWPRFS89wPQTMQjKoEmmmiiiSaaaLaNZhh6NF9rvRC83EAzhOaGF+ApbaIZQnPdq1SOJKrV2sZWolrb6kUzlKZ5kXmeqVa8mld4XitsbTYyGM09mvGdamk7YbZ3/Jdn/kFz/5obxvO2t4x5USnWzHq8UmxgLJp7RRIJ/80/KvnjGhuLpjA00UQTTTTRRBNNNNFEE0000UQTTTTRRBNNNNFEE0000UQTTTTRRBNNNNFE8z/NyIpSM7KCmqQKTWVoKkNTGZrK0FSGpjI0laGpDE1laCr7F05L8Sz5B9zGAAAAAElFTkSuQmCC)

<br>

#### 템플릿 영역을 만들어 배치하기
템플릿 영역으로 항목을 배치하면 그리드 레이아웃을 만드는 것보다 더 쉬움. 
```css
.box1{
  background-color: 3689ff;
  grid-area: box1;
}
.box2{
  background-color: #00cf12;
  grid-area: box2;
}
.box3{
  background-color: #ff9019;
  grid-area: box3;
}
.box4{
  background-color: #ffd000;
  grid-area: box4;
}
``` 

이어서 그리드 컨테이너로 사용하는 #wrapper 요소에서 gird-template-areas 속성을 사용해 템플릿 영역을 어떻게 배치할지 지정함. 템플릿 영역을 비워두려면 그 자리에 마침표(.)을 넣음. 한 줄에 들어갈 템플릿 영역을 큰따옴표("")로 묶어 주면되고 한줄마다 줄 바꿈을 하면 마치 눈으로 보듯 템플릿 영역을 나열할 수 있어서 좀 더 쉽게 작성할 수 있음.
```css
#wrapper{
  width: 700px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3,100px);
  grid-template-areas:
  "box1 box1 box1"
  "box2 box3 box3"
  "box2 . box4";
}
```