# 연산
---
연산자는 하나 이상의 표현식을 대상으로
산술, 할당, 비교, 논리, 타입, 지수 연산 등을 수행해
하나의 값을 만든다.
이때의 연산 대상을 ```피연산자(operand)```라고 한다.

```피연산자```는 값으로 평가될 수 있는 ```표현식```이어야 한다.
그리고 피연산자와 연산자로 이루어진 연산자 표현식도 값으로 평가될 수 있는 ```표현식```이다.

<br>

# 연산자 종류
---
```js
// 1. 산술 연산자
5 * 4 // -> 20
```
```js
// 2. 문자열 연결 연산자
'My name is' + 'Yang' // -> 'My name is Yang'
```
```js
// 3. 할당 연산자
color = 'red'	// -> 'red'
```
```js
// 4. 비교 연산자
3 > 5 			// -> false
```
```js
// 5. 논리 연산자
true && false 	// -> false
```
```js
// 6. 타입 연산자
typeof 'Hi' 	// -> string
typeof 3		// -> number
```

<br>

---
## 1. 산술 연산자
```js
5 + 3	// -> 8
5 - 3	// -> 1
5 * 3	// -> 15
5 / 3	// -> 1
5 % 3	// -> 1
```

<br>

### 단항 산술 연산자
```js
// 단항 산술 연산자
1++		// -> 2
5--		// -> 4
```
```js
var x = 5, result;

// 선할당 후증가(postfix increment operator)
result = x++;
console.log(result, x);	// 5 6

// 선증가 후할당(prefix increment operator)
result = ++x;
console.log(result, x); // 7 7

// 선할당 후감소(postfix decrement operator)
result = x--;
console.log(result, x); // 7 6

// 선감소 후할당(prefix decrement operator)
result = --x;
console.log(result, x); // 6 5
```

<br>

### 문자열 -> 숫자
```js
var x = '1';

// 문자열 -> 숫자
console.log(+x);		// 1
// 부수 효과 X
console.log(x);			// "1"

// 불리언 -> 숫자
x = true;
console.log(+x)			// 1
// 부수 효과 X
console.log(x)			// true

// 불리언 -> 숫자
x = false;
console.log(+x)			// 0
// 부수 효과 X
console.log(x)			// false

// 문자열 -> 숫자 불가능할땐 NaN 반환
// 문자열이 숫자로 구성되어 있을때만 변경 가능
x = 'Hello';
console.log(+x);		// NaN
console.log(x);			// "Hello"
```
앞에 ```+```를 붙여 숫자로 변환시키는 것은 자주 사용한다.

<br>

---


## 2. 문자열 연결 연산자
```js
// 문자열 연결 연산자
'1' + 2;			// '12'
1 + '2';			// '12'
123 + '';			// '123'
```

<br>

### 타입 변환
```js
// true는 1로 타입 변환됨
1 + true;			// 2

// false는 0으로 타입 변환됨
1 + false;			// 1

// null은 0으로 타입 변환됨
1 + null;			// 1

// undefined는 숫자로 타입 변환 불가능
+undefined;			// NaN
1 + undefined;		// NaN
```
<br>

---
## 3. 할당 연산자


+ 표현식인 문 : 값으로 평가될 수 있는 문

```js
var x;

// 할당문은 표현식인 문
console.log(x = 10);		// 10
```

<br>

---
## 4. 비교 연산자
### 동등 비교 연산자
```js
// 동등 비교
5 == 5;			// true

// 타입은 다르지만 압묵적 타입 변환을 통해 타입을 일치시키면 동등함
// 어느 것을 기준으로 타입을 일치시키는지는 js엔진에 따라..
5 == '5';		// true
```
<br>

### 일치 비교 연산자
```js
// 일치 비교
1 === '1'		// false
0 === false		// false
```
```js
// 주의할 점 : NaN는 자신과 같지 않은 유일한 값이다!
NaN === NaN				// false
Number.isNaN(NaN)		// true
Object.is(NaN, NaN)		// true
```
암묵적 타입 변환을 하지 않고 값을 비교하기 때문에 정확하다.
따라서 동등 비교 연산자보다 일치 비교 연산자를 쓰는 것을 권장한다.

<br>

#### isNaN()
```js
isNaN(NaN)			// true
isNaN(undefined)	// true
isNaN(null)			// false
isNaN(-NaN)			// true / -NaN은 NaN와 같다
isNaN({})			// true
```
보다시피 ```isNaN()```은 문제가 있다.
```undefined```, ```{}```도 ```NaN```으로 판단한다.

<br>

#### Number.isNaN()
```js
Number.isNaN({})		// false
Number.isNaN(NaN)		// true
Number.isNaN(+'123sdf') // true
```
ES6에 나온 ```Number.isNaN()```은 ```isNaN()```보다 정확하다.
```Number```에서 숫자가 아닌 것을 걸러주기 때문!
```Number.isNaN()```을 사용하는 것을 권장한다.

<br>

#### Object.is()

```js
0 === -0		// true
0 == -0			// true
Object.is(0, -0)		// false
```
> 아무튼 가장 정확한 비교는 늘 ```Object.is()```를 사용하자!

<br>

### 대소 비교 연산자
```js
// >, >=, <, <= 이런 것들..
```

<br>

### 삼항 연산자
```js
var x = 2;

// 2 % 2 는 0이고 0은 false로 암묵적 타입 변환된다.
var result = x % 2 ? '홀수' : '짝수';

console.log(result);	// 짝수
```
```js
var x = 10;

// if ...else 문은 표현식이 아닌 문이다.
// 따라서 값처럼 할당할 수 없다.
var result = if (x % 2) { result = '홀수'; } else { result = '짝수'; };
// SyntaxError : Unexpected token if
```

<br>

---

## 5. 논리 연산자
### 논리합 연산자
```js
// 논리합 (||) 연산자
true || true;		// true
true || false; 		// true
false || true;		// true
false || false;		// false;
```
평가 진행 방향 : 좌항 -> 우항
논리합 연산자는 하나가 ```true```이면 ```true```를 리턴한다.
따라서 하나가 ```true```라는 것을 확인하면 뒤에 것을 평가할 필요 없이 ```true```를 리턴하게 된다.

<br>

### 논리곱 연산자
```js
// 논리곱 (&&) 연산자
true && true;		// true
true && false;		// false
false && true;		// false
false && false;		// false
```
평가 진행 방향 : 좌항 -> 우항
논리곱 연산자는 앞이 ```true```여야만 뒤에 것을 평가한다.
따라서 앞이 ```false```라는 것을 확인하면 뒤에 것을 평가할 필요 없이 ```false```를 리턴하게 된다.

<br>

### 논리 부정 연산자
```js
// 논리 부정 (!) 연산자
!true;		// false
!false;		// true

// 형변환 활용
!(!true);	// true
!!1;		// true
!!'';		// false | 빈 문자열은 false의 값을 가진다.
```

<br>

### 단축 평가
```js
// 단축 평가
'Cat' && 'Dog';		// 'Dog'
```
평가 진행 방향 : 좌항 -> 우항
첫 번째 피연산자 'Cat'은 Truthy 값이므로 true로 평가됩니다. 하지만 위 표현식은 이 시점에서 평가할 수 없습니다. 두 번째 피연산자까지 평가해 보아야합니다. 즉, 두 번째 피연산자가 논리곱 연산자 표현식의 평가 결과를 결정하며, 논리곱 연산자는 논리 연산의 결과를 결정하는 두 번째 피연산자 'Dog'를 그대로 반환합니다.

<br>

### 드모르간 법칙
```js
// 드모르간 법칙
!(x || y) === (!x && !y)
!(x && y) === (!x || !y)
```

<br>

### 컴마 연산자
```js
// 컴마 연산자
var x, y, z;

x = 1, y = 2, z = 3;	// 3
```
```js
// 컴마 연산자는 앞 -> 뒤 로 실행되면서
// 마지막 오는 것을 값으로 평가한다.
function a() {
  var x, y;
  return x = 1, y = 2, console.log(x), console.log(y), console.log(x + y);
}

a()
// 1
// 2
// 3
```

<br>

---

## 6. 타입 연산자
```js
typeof ''				// "string"
typeof 1				// "number"
typeof NaN				// "number"
typeof true				// "boolean"
typeof undefined		// "undefined"
typeof Symbol()			// "symbol"
typeof null				// "object"
typeof []				// "object"
typeof {}				// "object"
typeof new Date()		// "object"
typeof /test/gi			// "object"
typeof function () {}	// "function"
```
타입을 리턴해준다.

<br>

---

## 그 외 연산자

### 지수 연산자
```js
Math.pow(2, 2);		// 4
2 ** 2;				// 4
Math.pow(3, 2);		// 9
3 ** 2;				// 9

// **= 도 가능하다
var x = 3
x **= 2				// 9
```

<br>

### 옵셔널 체이닝 연산자
```js
// 다음과 같이 obj1, obj2 객체가 있다고 가정하자
const obj1 = {
  a : {
    b : {
      c : {
        d : 1
      }
    }
  }
}
  
const obj2 = {
  a : {
    b : 0
  }
}
```
```js
// ?는 앞에 있는 것이 존재하지 않으면 undefined를 리턴한다
obj1.a?.b?.c?.d		// 1
obj2.a?.b?.c?.d		// undefined
```
```js
// obj2.a.b.c는 값이 없는 것으로 판단이 됨
// 따라서 a에는 10이 할당되어진다
const a = obj2.a.b.c ?? 10;
a			// 10

// obj2.a.b 는 0의 값을 가지므로
// b에는 0이 할당되어진다
const b = obj2.a.b ?? 10;
b			// 0
```

<br>

### delete, in, new, instanceof 연산자
```js
// instanceof 연산자
[] instanceof Array		// true
```
```js
//  in 연산자
// 객체에 특정 프로퍼티가 존재하는지
'a' in obj				// true
```
```js
// delete 연산자
// 객체의 프로퍼티를 삭제하는 부수 효과가 있다
// 이는 o 객체를 사용하는 다른 코드에 영향을 준다
var o = { a : 1 };

delete o.a;
console.log(o);		// {}
```

<br>

---

## 연산자 우선순위

우선순위를 매기기 애매할때는 괄호로 묶어주자..
요즘은 ```prettier```가 알아서 해준다!

<br>

---

## 연산자 평가 방향
할당 연산자는 ```우항 -> 좌항```
그 외 연산자들은 모두 ```좌항 -> 우항``` 이라고 생각하면 편할듯!

<br>