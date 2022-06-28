# 스타일과 스타일 시트
CSS 소스에서 한 줄이 하나의 스타일에 해당하고, 조금 더 들여다보면 줄마다 형태가 비슷하다는 걸

```
선택자 { 속성1: 속성값1; 속성2: 속성값2}
```
맨 앞의 선택자는 스타일을 어느 태그에 적용할 것인지 알려 주는 것이고 줄괄호({})사이에는 스타일 정보를 넣음

```css
p{
  text-align: center;
  color:blue;
}
```

```css
p{ /*css 여러 줄로 표기하기*/
  text-align: center;
  color: blue;
}

p{text-align: center; color: blue;} /*css 한 줄로 표기하기
```

### CSS 소스 경량화
```
CSS 소스에 주석을 넣거나 줄 바꿈하는 것은 웹 사이트 작성자가 알아보기 쉽도록 하는 것일 뿐 웹 브라우저에는 아무 의미가 없음. 웹 브라우저에서 CSS 소스를 읽을 때는 선택자와 속성, 그리고 속상값만 의미가 있음. CSS 소스는 네트워크를 이용해 파일로 내려받으므로 되도록이면 파일 크기가 작은 것이 좋음. 이것을 CSS 소스 경량화라고 함.(CSS compress)
```

## 스타일 시트
웹 문서는 스타일 규칙을 여러 개 사용함. 이런 스타일 규칙을 한눈에 확인하고 필요할 때마다 수정하기도 쉽도록 한군데 묶어 놓은 것을 스타일 시트라고 함.
- 스타일 시트는 크게 웹 브라우저에 기본으로 만들어져 있는 부라우저 기본 스타일과 사이트 제작자가 만든 사용자 스타일로 나눌 수 있음.

- 간단한 스타일 정보라면 스타일 시트를 사용하지 않고 바로 스타일을 적용할 대상에 직접 표시하는데 이걸 인라인 스타일 이라고 함.(html 내부에서)
    ```css
    style="color: blue;"
    ```

- 웹 문서 안에서 사용할 스타일을 같은 내부에서 문서 안에 정리한 것을 내부 스타일 시트라고 함

```html
    <style>

      h1{
        padding: 10px;
        background-color: #222;
        color: #fff;
      }

    </style>
```

- 여러 웹 문서에서 사용할 스타일을 별도 파일로 저장해 놓고 필요할 때 마다 가져와서 사용하는 것이 일반적인데, 이렇게 따로 저장해 놓은 스타일 정보를 외부 스타일 시트라고 한다.

```html
<link rel="stylesheet" href="css/style.css">
```

### 전체 선택자
```css
*{
  margin: 0;
}
```

### 태그와 요소의 차이
```
태그는 말 그대로 태그 자체를 가리키는 반면, 요소는 태그를 적용한 것을 가리킴.
    <p>텍스트 단락 지정하기<p>
이 소스에서 <p>와 </p>태그는 태그 자체를 말하는 것이고 태그를 포함해 <p> 태그를 적용한 '텍스트 단락 지정하기'부분을 p요소 라고 함.
```

### 특정 요소에 스타일을 적용하는 타입 선택자
```css
p {
  font-style: italic;
}
```

### 타입 선택자와 태그 선택자의 차이점
```
타입 선택자는 태그 이름을 선택자로 사용하므로 태그 선택자라고도 하고, 스타일을 적용하는 대상이 요소이므로 요소 선택자 라고함.
```

### 특정부분에 적용하는 클래스 선택자
```html
<style>
  .accent {
    border: 1px solid #000;
  }
  .bg{
    background-color: #ddd;
  }
</style>

<h1 class="accent bg">레드향</h1> <!-- accent와 bg클래스 선택자 사용 -->
<span class="accent">레드향</span> <!-- accent 클래스만 사용 -->
```

### 특정 부분에 스타일을 한번만 적용할 수 있는 Id 선택자
```html
<style>
  #container{
    width: 500px;
    margin: 10px auto;
    padding: 10px;
    border: 1px solid #000;
  }
</style>
<div id="container">
  <h1>레드향</h1>
```

### 같은 스타일 규칙을 사용하는 요소들을 묶는 그룹 선택자
```css
h1,p{
  text-align: center;
}
```

## 캐스케이딩 스타일 시트

CSS에서 'C'는 캐스케이딩의 줄임말이며 스타일 시트에서는 우선순위가 위에서 아래, 즉 계단식으로 적용된다는 의미로 사용됨.그래서 CSS에서는 웹 요소에 둘 이상의 스타일을 적용할 때 우선순위에 따라 적용할 스타일을 결정함. 캐스케이딩은 스타일끼리 충돌하지 않도록 막아주는 중요한 개념임. 캐스케이딩은 스타일끼리 충돌하지 않도록 막아주는 중요한 방법 2가지 방법이 있음

```
- 스타일 우선순위 : 스타일 규칙의 중요도와 적용 범위에 따라 운선순위가 결정되고, 그 우선순위에 따라 위에서 아래로 스타일을 적용함.

- 스타일 상속 : 태그의 포함 관계에 따라 부모 요소의 스타일을 자식 요소로, 위에서 아래로 전달함.
```

### 스타일 우선순위
우선순위란 어떤 스타일 먼저 적용할 것인지 결정하는 규칙을 말함. 위 3가지 개념에 따라 지정됨

  1. 사용자 스타일
  2. 제작자 스타일
  3. 브라우저 기본 스타일

위 순서는 브라우저 스타일 순으로 나열한것임. 만약 중요도가 같은 스타일이라면 스타일 적용 범위에 따라 우선순위를 정할 수 있음.  스타일 적용범위가 좁을수록, 즉 정확히 필요한 요소에만 적용할 스타일일수록 우선순위가 높아짐

```
- !important : 어떤 스타일보다 우선 적용하는 스타일

- 인라인 스타일 : 태그 안에 style 속성을 사용해 해당 태그만 스타일을 적용

- id 스타일 : 지정한 부분에만 적용되는 스타일이지만 한 문서에 한번만 적용 가능( 선택자 앞에 #)

- 클래스 스타일 : 웹 문서에서 지정한 부분에만 적용되는 스타일로 한 문서에 여러번 적용할 수 있음 

- 타입 스타일 : 웹 문서에 사용한 특정 태그에 스타일을 똑같이 적용함
```

### 스타일 상속
웹 문서에서 사용하는 여러 태그는 서로 포함 관계가 있음. 이때 포함하는 태그를 부모 요소, 포함된 태그를 자식 요소라고 하고 스타일 시트에서는 자식 요소에서 별도로 스타일을 지정하지 않으면 부모요소의 스타일 속성들이 자식 요소로 전달되는데 이것을 스타일 상속 이라고함<br>
(참고로 배경색과 배경 이미지는 스타일 상속이 되지 않음. 또한 스타일 상속만으로는 모든 스타일의 충돌을 해결할 수 없음. 만약 부모 요소로부터 글꼴을 상속받은 자식 요소에서 다른 글꼴을 사용하려면, 명시도, 소스 순서에 따라 해결해야함)

<br>
<br>

# 텍스트 표현 스타일

### 글꼴 지정하는 font-family
```css
body { font-family: "맑은고딕", 돋움, 굴림} /*문서 전체 적용*/
```
```
- font-size: <절대 크기>|<상대크기>|<크기>|<백분율>

- 절대크기 : 브라우저에서 지정한 글자크기

- 상대크기 : 부모 요소의 글자 크기를 기준으로 상대적인 글자 크기를 지정

- 크기 : 브라우저와 상관없이 글자 크기를 직접 지정

- 백분율 : 부모 요소의 글자 크기를 기준으로 백분율(%)로 표시
```

### 이탤릭체로 글자를 표시하는 font-style 속성
```
font-style : normal | italic | oblique
```

### 글자 굵기를 지정하는 font-weight 속성
```
font-weight : normal | bold | bolder | lighter | 100 | 200 | ... | 800 | 900
```

```css
body{
  font-size: 20px;
}
h1{
  font-family: 바탕;
  font-size: 3em;
}
.accent{
  font-size: 150%;
  font-weight: 800;
}
.italic{
  font-style: italic;
}
```
<br>

## 웹 폰트 사용하기
사용자 시스템에 없는 글꼴이더라도 웹 문서를 만들 때 사용한 글꼴을 내려받은 후 표시하므로 웹 제작자가 의도한 대로 텍스트를 보여 줄 수 있음.

### 웹 폰트 업로드
```css
@font-face{
  font-family : 'Ostrich';
  src: local('Ostrich Sans'),
        url('fonts/ostrich-sans-bold.woff') format('woff'),
        url('fonts/ostrich-sans0bold.ttf') format('truetype'),
        url('fonts/ostrich-sans0bold.svg') format('svg'),
}
.wfont{
  font-family: 'Ostrich', sans-serif; /*웹 폰트 지정 */
}
```

## 텍스트 관련 스타일

### 글자색 color
```css
h1{
  color: #0000ff;
}
```

### rgb 표기법으로 파란색 지정하기
```css
h1{color: rgb(0, 0, 255);}
```

### rgba 표기법으로 불투명도 지정하기
```css
h1 { color: rgba(0, 0, 255, 0.5);}
```

### 텍스트를 정렬하는 text-align 속성 
```
start : 현재 텍스트 줄의 시작 위치에 맞추어 문단을 정렬
end : 현재 텍스트 줄의 끝 위치에 맞추어 문단을 정렬
left : 왼쪽에 맞추어 문단을 정렬
right : 오른쪽에 맞추어 문단을 정렬
center : 가운데에 맞추어 문단을 정렬
justify : 양쪽에 맞추어 문단을 정렬
match-parent : 부모 요소를 따라 문단을 정렬
```
```css
.center{
  text-align : center;
}
.justify{
  text-align : justify;
}
```

### 줄 간격을 조절하는 line-hight 속성
```css
p { font-size: 12px; line-height: 24px;}
p { font-size: 12px; line-height: 2.0;}
p { font-size: 12px; line-height: 200%;}
```

### 텍스트에 그림자 효과를 추가하는 text-shadow 속성
```css
.shaodw1{
  text-shadow: 1px 1px black; /*가로, 세로거리, 색상지정*/
}
```

### 글자 간격 조절하기
```css
.spacing1{
  letter-spacing: 0.2em;
}
```

<br>

# 레이아웃을 구성하는 CSS 박스 모델

## 블록 레벨 요소와 인라인 레벨 요소
박스 모델은 블록 레벨 요소인지 인라인 레벨 요소인지에 따라 나열 방법이 달라짐.
- 블록 레벨 요소 : 태그를 사용해 요소를 삽입했을 때 혼자 한 줄을 차지하는 것을 가리킴.
```html
<h1>시간이란...</h1>
<div>내일 죽을 것처럼 <p class="accent">오늘</p>을 살고</div>
<p>영원히 살 것처럼<br>내일을 꿈꾸어라.</p>
```
- 인라인 레벨 요소 : 콘텐츠만큼만 영역을 차지하고 나머지 공간에는 다른 요소가 옴
```html
<h1>시간이라...</h1>
<div>내일 죽을 것처럼 <span class="accent">오늘</span>을 살고</div>
<p>
```

## 박스 모델의 기본 구성
마진(margin)<br>
테두리(border)<br>
패딩(padding)<br>
콘텐츠영역<br>

```css
.box1{
  width: 400px;
  height: 100px;
}
```

## 요소 주변의 여백을 설정하는 margin 속성
margin은 요소 주변의 여백을 의미, 즉 마진을 이용하면 요소와 요소 사이의 간격을 조절할 수 있음.

### margin 속성으로 여백 설정하기
```css
#margin1 { margin: 50px; } /* 상하좌우 4개 방향의 마진 모두 50px */
#margin2 { margin: 30px 50px; } /* 위 아래 마진30px, 좌우 마진 50px */
#margin3 { margin: 30px 20px 50px; } /* 위 마진 30px, 좌우 마진 20px, 아래 마진 50px */
#margin4 { margin: 30px 50px 30px 50px;} /* 위 아래 마진 30px, 좌우 마진 50px */
```

### 웹 문서 전체를 웹 브라우저 화면 중앙에 배치하기
```css
body { background-color: #222;} /*배경색은 어둡게 지정 */
#container{
  background-color: #fff;
  width: 600px; /*가로 너비 600px */
  margin: 20px auto;  /*위아래 마진은 20px씩, 좌우 마진은 자동 계산*/
  padding: 20px;
}
```

## 마진 중첩 이해하기
박스 모델에서 마진을 지정할 때 요소를 세로로 배치할 경우 각 요소의 마진과 마진이 서로 만나면 마진값이 큰 쪽으로 겹쳐지는데, 이것을 마진 중첩 또는 마진 상쇄라고 함.
```css
div{
  width: 200px;
  height: 100px;
  margin: 30px;
}
#box1 {background: rgb(0,77, 243);}
#box2{background: rgb(255,72,0);}
```

## 콘텐츠와 테두리 사이의 여백을 설정하는 padding
padding 이란 콘텐츠 영역과 테두리 사이의 여백을 말함, 즉 테두리 안쪽의 여백이라고 생각하면 됨. 패딩과 마진은 여백이 어느 위치에 있느냐만 다를 뿐 박스 모델에서 패딩을 지정하는 방법은 마진과 거의 같음.

```css
#padding1{
  padding: 20px 30px 40px 50px;
}
#padding2{
  padding: 20px 30px;
}
#padding3{
  padding:
}
```

## 배치 방법 결정하는 display 속성
display 속성을 사용하면 블록 레벨 요소와 인라인 레벨 요소를 서로 바꿔서 사용이 가능함. display 속성은 주로 웹 문서의 내비게이션을 만들면서 메뉴 항목을 가로로 배치할 때 많이 사용하고, 이미지를 표 형태로 배치할 수도 있음.
```
block : 인라인 레벨 요소를 블록 레벨 요소를 만듬
inline : 블록 레벨 요소를 인라인 레벨 요소로 만듬
inline-block : 인라인 레벨 요소와 블록 레벨 요소의 속성을 모두 가지고 있으며 마진과 패딩을 지정할 수 있음
none : 해당 요소를 화면에 표시하지 않음
```
```css
*{
  box-sizing: border-box;
}
nav ul{
  list-style: none;
}
nav ul li{
  display: inline-block; /*인라인 레벨 요소와 블록 레벨 요소 모두 지정*/
  padding: 20px;
  margin: 0 20px;
  border: 1px solid #222; /*메뉴의 테두리 지정 */
}
```

### 왼쪽이나 오른쪽으로 배치하는 float 속성
```
웹 문서를 만들다 보면 <p>태그처럼 문단의 왼쪽이나 오른쪽에 이미지를 나란히 표시해야 할 경우가 있음. 근데 <p>는 블록 레벨 요소 이므로 이미지와 나란히 한줄에 배치가 불가능함. 이때 float 속성을 사용하여 이미지를 표시하고 그 주변에 텍스트가 둘러 싸도록 할 수 있음.
```
```css
img{
  float: left;
  margin-right
}
```

### float 속성을 해제하는 clear 속성
```css
#box1{
  background: #ffd800;
  float: left;
}
#box2{
  background: #0094ff;
  
}
#box3{
  background: #00ff21;
}
#box4{
  background: #a874ff;
  clear: left;
}
```
```
display: inline-block은 가로로 배치하면서도 기본 마진과 패딩을 가지고 있지만, float: left로 배치하면 가로로 배치될 때 요소에 기본 마진과 패딩이 없음. 그래서 필요하다면 요소마다 마진과 패딩을 지정해야 함. 그리고 float: leftf를 사용하면 clear속성으로 플로팅을 해제해야 함.
```
2단 레이아웃<br>
![2way-layout](../img/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202022-06-24%20%EC%98%A4%ED%9B%84%203.41.47.png)

3단 레이아웃<br>
![3way-layout](../img/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202022-06-24%20%EC%98%A4%ED%9B%84%203.42.02.png)

<br>
<br>

### 웹 요소의 위치를 정하는 left,right,top,bottom 속성
```
left : 기준 위치와 요소 사이에 왼쪽으로 얼마나 떨어져 있는지 지정
right : 기준 위치와 요소 사이에 오른쪽으로 얼마나 떨어져 있는지 지정
top : 기준 위치와 요소 사이에 위쪽으로 얼마나 떨어져 있는지 지정
bottom : 기준 위치와 요소 사이에 아래쪽으로 얼마나 떨어져 있는지 지정
```
```css
#pos1 {
  position: absolute;
  left: 50px;
  top: 50px;
}
#pos2{
  position: absolute;
  right: 100px;
  top: 100px;
}
#pos3{
  position: absolute;
  left: 100px;
  bottom: 100px;
}
```

### 배치 방법을 지정하는 Postion 속성
```
static : 문서의 흐름에 맞춰 배치함. 기본값임.
relative : 위칫값을 지정할 수 있다는 점을 제외하면 static과 같음.
absolute : relative값을 사용한 상위 요소를 기준으로 위치를 지정해 배치함.
fixed : 브라우저 창을 기준으로 위치를 지정해 배치함.
```

### background-color 속성
```css
background-color: #008000;
background-color: rgb(0,128,0);
background-color: green;
```
글꼴이나 글자 크기는 body태그 선택자에서 지정하면 문서 전체에 상속됨. 하지만 예외로 background-color값은 상속되지 않음. 기본적으로 모든 웹 문서 요소의 배경은 투명함.

예를들어 body 태그 선택자에 파란색 배경색 스타일을 넣으면, 그 안에 있는 div, p등의 요소에도 마치 파란색이 적용된 것처럼 보임. 하지만 div, p 등의 요소는 기본적으로 기본적으로 투명하므로 그렇게 보이는 것일 뿐 body 태그 선택자의 배경 스타일이 상속된 것은 아님.

<br>
<br>

### 배경색의 적용 범위를 조절하는 background-clop 속성
```
border-box : 박스 모델의 가장 외곽인 테두리까지 적용함. 기본값임.
padding-box : 박스 모델에서 테두리를 뺀 패딩 범위까지 적용함.
content-box : 박스 모델에서 내용(콘텐츠) 부분에만 적용함.
```

### 웹 요소에 배경 이미지를 넣는 background-image 속성
```
background-image: url('이미지 파일 경로')
```

### 배경이미지 반복 방법을 지정하는 background-repeat 속성
```
repeat : 브라우저 화면에 가득 찰 때까지 가로, 세로로 반복함. 기본값임.
repeat-x : 브라우저 화면 너비에 가득 찰 때까지 가로로 반복
repeat-y : 브라우저 화면 높이에 가득 찰 때까지 세로로 반복
no-repeat : 한 번만 표시하고 반복하지 않습니다.
```

### 배경 이미지의 적용 범위를 조절하는 background-origin 속성
```
content-box : 박스 모델에서 내용 부분에만 배경 이미지를 표시함. 기본값임.
padding-box : 박스 모델에서 패딩까지 배경 이미지를 표시함.
border-box : 박스 모델에서 테두리까지 배경 이미지를 표시함.
```

### 배경 이미지를 고정하는 background-attachment 속성
```
scroll : 화면을 스크롤하면 배경 이미지도 스크롤됨. 기본값임.
fixed : 화면을 스크롤하면 배경 이미지는 고정되고 내용만 스크롤됨.
```

### background 속성 하나로 배경 이미지 제거하기
```css
background: url('images/bg4.png') no-repeat center bottom fixed;
```

### 배경 이미지 크기를 조절하는 background-size 속성
```
auto : 원래 배경 이미지 크기만큼 표시함. 기본값임.
contain : 요소 안에 배경 이미지가 다 들어오도록 이미지를 확대,축소함.
cover : 배경 이미지로 요소를 모두 덮도록 이미지를 확대,축소함.
<크기> : 이미지의 너비와 높이를 지정함. 값이 하나만 주어질 경우 너빗값으로 인식하며, 이미지의 너비와 너빗값에 맞춘 높잇값도 자동 계산함.
<백분율> : 배경 이미지가 들어갈 요소의 크기를 기준으로 값을 백분율로 지정하고 그 크기에 맞도록 배경 이미지를 확대, 축소함.
```
```css
  .box{
    width: 300px;
    height: 300px;
    margin: 20px;
    background: url('images/bg4.jpg') no-repeat left top; /*배경 이미지를 반복하지 않고 왼쪽 상단에 위치*/
  }
  #bg1{
    background-size: auto; /*원래 배경 이미지 크기로 표시 */
  }
  #bg2{
    background-size:200px; /*너비는 200px, 높이는 자동 계산 */
  }
  #bg3{
    background-size:50%;
  }
  #bg4{
    background-size:100% 100%; /*요소의 너비와 높이를 100% 맞춤 */
  }
```

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
