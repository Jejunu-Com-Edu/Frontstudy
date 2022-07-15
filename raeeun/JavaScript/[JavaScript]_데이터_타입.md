# JavaScript의 타입
---
7가지 데이터 타입이 존재한다.

1) 숫자 (number)
2) 문자열 (string)
3) 불린값 (boolean)
4) undefined
5) null
6) 심벌 (symbol)
7) 객체 (object)

<br>

## 1. 숫자(number) 타입
---
```js
// 모두 숫자 타입
var integer = 10;	// 정수
var double = 10.12; // 소수
var negative = -20; // 음수
```
```js
var binary = 0b01000001; // 2진수
var octal = 0o101;		 // 8진수
var hex = 0x41;			 // 16진수

// 표기법만 다를 뿐 모두 같은 값임 
console.log(binary);	 // 65
console.log(octal);		 // 65
console.log(hex);		 // 65
console.log(binary === octal) // true
console.log(octal === hex) 	  // true
```
```js
// 숫자 타입은 모두 실수로 처리됨
console.log(1 === 1.0);	// true
console.log(4 / 2);		// 2
console.log(3 / 2);		// 1.5
```
```js
console.log(0 === -0)	// true
Object.is(0, -0)		// false
```
```js
// 숫자 타입의 세 가지 특별한 값
console.log(10 / 0);		// Infinity
console.log(10 / -0);		// -Infinity
console.log(1 * 'String');	// NaN 
```
```js
// BigInt는 Number 원시 값이 안정적으로 나타낼 수 있는 최대치인 2^53 - 1보다 큰 정수를 표현할 수 있는 내장 객체
1324293794532n === BigInt(1324293794532n)	// true
```

<br>

## 2. 문자열(String) 타입
---
```js
string = '문자열'; 	// 작은따옴표
string = "문자열";		// 큰따옴표
string = `문자열`;		// 백틱 (ES6)

string = '작은따옴표로 감싼 문자열 내의 "큰따옴표"는 문자열로 인식함';
string = "큰따옴표로 감싼 문자열 내의 '작은따옴표'는 문자열로 인식함";
```
```js
// 따옴표로 감싸지 않은 hello는 식별자로 인식함
var string = hello;	// ReferenceError : hello is not defined.
```

### 템플릿 리터럴
```js
// 템플릿 리터럴을 사용하면 줄바꿈 가능, ${}로 변수 넣기 가능
// 원래는 줄바꿈 허용 X 백틱을 쓰면 줄바꿈 허용!!
var num = 123;
var template = `template
literal
num is ${num}`;

console.log(template);
// template
// literal
// num is 123
```
### 이스케이프 시퀀스
```js
// '또는 "를 출력하고 싶을 때, \' 또는 \"와 같이 사용하면 됨
// \n \t \b 이런게 이스케이프 시퀀스
```

<br>

## 3. 불린(Boolean) 타입
---
```js
var foo = true;
console.log(foo);	// true

foo = false;
console.log(foo);	// false
```

<br>

## 4. undefined 타입
---
```js
// 값을 지정하지 않았을때 자동으로 undefined가 할당
var foo;
console.log(foo);	// undefined
```
un + defined : define(정의)되지 않음!
>변수 : "선언한다" 라고 표현
함수 : "정의한다" 라고 표현

<br>

## 5. null 타입
---

```js
// 변수에 값이 없다는 것을 명시하고 싶을땐? null 타입을 쓰자!
var foo = 'Lee';

// 함수가 유효한 값을 반환할 수 없는 경우 null을 반환하기도 한다.
// 이전에 할당되어 있던 값에 대한 참조를 제거.
// 유용해 보이지는 않음.
```
함수가 유효한 값을 반환할 수 없는 경우 null을 반환하기도 한다.
예를 들어, ```Html```요소를 검색해 반환하는 ```document.querySelector```는 조건에 부합하는 것을 반환할 수 없는 경우 error대신 null을 반환한다.
```js
document.querySelector('.a');	// null
```

<br>

## 6. 심벌(Symbol) 타입 (ES6)
---
```심벌(symbol)``` : 변경 불가능한 원시 타입, **다른 값과 절대 중복되지 않는 유일무이한 값**.
```js
Symbol('abc') === Symbol('abc')	// false
```
```js
var a = Symbol('abc');
var b = Symbol('abc');
console.log(a === b);	// false
```
```js
Symbol() // 개발자가 구분하기 위한 label으로써 사용된다.
// 안에 어떤 값이 들어가던 어쨌든 절대로 중복되지 않으니까..
```

어쨌든 충돌할 일이 없으니 Symbol()을 객체의 프로퍼티 키로 쓰면 좋다
```js
// 심벌 값 생성
var key = Symbol('key');
console.log(typeof key);	// symbol

// 객체 생성
var obj = {};

// 이름이 충돌할 위험이 없는 유일무이한 값인 심벌을 프로퍼티 키로 사용한다
obj[key] = 'value';
console.log(obj[key]); 	// value
```

<br>

## 7. 객체(Object) 타입
---
```숫자```, ```문자열```, ```불린```, ```undefined```, ```null```, ```symbol``` 타입을 제외한 모든 것은 객체 타입이다.

### 메모리 공간의 확보와 참조
```js
// 이런게 있다고 했을때
var a = 100;
var b = 100;

// 값은 메모리에 할당
0x123 : 100

// 식별자 a와 b 위치는 따로 있지만 같은 주소 0x123을 참조함
0x111 : 식별자 a, 값 0x123
0x112 : 식별자 b, 값 0x123

// 만약 b의 값이 바뀐다면??
b = 111;

0x124 : 111
0x112 : 식별자 b, 값 0x124
```
위처럼 100이라는 값의 **메모리 주소**를 참조하는 이유:
그렇지 않으면.. 크기가 매우 큰 값들이 무분별하게 메모리 공간을 차지할 수 있음!
예를 들어.....
```js
// 이럴 경우 엄청긴 문자열 여러개가 메모리 공간에 할당되게 된다
// -> 공간 활용이 비효율적임!
var a = "엄청긴문자열"
var b = a;
var c = b;
var d = c;
```

<br>

# 정적 타입 언어 VS 동적 타입 언어
---
우선 JavaScript는 동적 타입 언어이다!
## 정적 타입 언어
C언어의 경우에는..
```c
// c 변수에는 1바이트 정수 타입의 값(-128 ~ 127)만을 할당 가능
char c;

// num 변수에는 4바이트 정수 타입의 값(-2,147,483,648~2,147,483,647)만을 할당 가능
int num;
```

## 동적 타입 언어
하지만 JavaScript의 경우, 그렇지 않다.
변수에 할당되는 타입을 정적으로가 아니라 동적으로 바꿀 수 있도록 한다.

**변수에 재할당을 할때마다 타입이 바뀐다!**
```js
var foo;
console.log(typeof foo);	// undefined

foo = 3;
console.log(typeof foo);	// number

foo = 'Hello';
console.log(typeof foo);	// string

foo = true;
console.log(typeof foo);	// boolean

foo = null;
console.log(typeof foo);	// null (object가 나오는 것은 버그)

foo = Symbol();
console.log(typeof foo);	// symbol

foo = {};	// 객체
console.log(typeof foo);	// object

foo = [];	// 배열
console.log(typeof foo);	// object

foo = function () {}; // 함수
console.log(typeof foo);	// function
```
JavaScript의 변수는 선언에 아닌 할당에 의해 타입이 결정된다.
재할당에 의해 변수의 타입은 언제든지 변할 수 있다
-> ```dynamic typing``` 이라고 함

자바스크립트는 동적 타입 언어이다!

> 변수는 type을 갖지 않고 값은 type을 갖는다.

변수에 타입이 있는 값을 할당함으로써 변수가 가지는 값의 타입이 동적으로 변경될 수 있음

<br>