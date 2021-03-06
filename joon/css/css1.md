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