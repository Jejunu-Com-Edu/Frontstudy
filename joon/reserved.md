# var, let, const 

Javascript에서 변수 선언 방식인 ```var```,```let```,```const```의 차이점에 대해 알아보자.

<br>
<br>

## 변수 선언 방식
우선, ```var```는 변수 선언 방식에 있어 큰 단점을 가지고 있음.(총정리에도 언급)
```js
var name = 'birthday'
console.log(name) //birthday

var name = 'javascript'
console.log(name) //javascript
```
변수를 한 번 더 선언했음에도 불구하고, 에러가 나오지 않고 각기 다른 값이 출력되는 것을 볼 수 있음.

위는 간단한 프로그램에서는 편할 수 있으나, 코드량이 많아지면 어디서 어떻게 사용될지 파악이 힘들뿐더러 값이 변할 수 있음.

그래서 ES6 이후, 이를 보완하기 위해 추가 된 변수 선언 방식이 ```let```, ```const```임.
```js
let name = 'birthday'
console.log(name) //birthday

let name = 'javascript'
console.log(name)
// Uncaught SyntaxError: Identifier 'name' has already been declared
```
```name```이 이미 선언되었다는 에러 메세지가 나옴.(```const```도 마찬가지)<p>
변수 재선언이 되지 않음.<p>
그러면 ```let```과 ```const```의 차이점은 무엇일까?
이 둘의 차이점은 ```immutable``` 여부임
```let```은 변수에 재할당이 가능함. 하지만,
```js
let name = 'birthday'
console.log(name) //birthday

let name = 'javascript'
console.log(name)
// Uncaught SyntaxError: Identifier 'name' has already been declared

name = 'react'
console.log(name) //react
```
```const```는 변수 재선언, 변수 재할당 모두 불가능함.
```js
    const name = 'birthday'
    console.log(name) // birthday

    const name = 'javascript'
    console.log(name) 
    // Uncaught SyntaxError: Identifier 'name' has already been declared

    name = 'react'
    console.log(name) 
    //Uncaught TypeError: Assignment to constant variable.
```

## 호이스팅
호이스팅이란, var 선언문이나 function 선언문 등을 해당 스코프의 선두로 옮긴 것처럼 동작하는 특성을 말함.<p>
(코드가 실행되기 전에 선언해둔 변수, 함수들이 뭐가 있는지 메모리에 기억을 해둠, 호이스팅시 변수의 선언과 초기화 ```undefined```로 같이 시켜버림)<p>

<br>

자바스크립트는 ES6에서 도입된 let, const를 포함하여 모든 선언(var, let, const, function, class, function*)을 호이스팅함.<p>

하지만, ```var```로 선언된 변수와는 달리 ```let```로 선언된 변수를 선언문 이전에 참조하면 참조 에러가 발생함.

```js
	console.log(foo); // undefined
	var foo;

	console.log(bar); // Error: Uncaught ReferenceError: bar is not defined
	let bar;
```
이는 ```let``로 선언된 변수는 스코프의 시작에서 변수의 선언까지 일시적 사각지대(Temporal Dead Zone)에 빠지기 때문임.<p>
(일시적 사각지대는 a가 선언 되었을때 초기화문이 나오기 전까지는 a를 사용할 수 없도록 하는 것)

참고로, 변수는 선언단계 > 초기화 단계 > 할당 단계에 걸쳐 생성되는데
```var```으로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어짐. 하지만,
```js
// 스코프의 선두에서 선언 단계와 초기화 단계가 실행된다.
// 따라서 변수 선언문 이전에 변수를 참조할 수 있다.

console.log(foo); // undefined

var foo;
console.log(foo); // undefined

foo = 1; // 할당문에서 할당 단계가 실행된다.
console.log(foo); // 1
```
```let```로 선언된 변수는 선언 단계와 초기화 단계가 분리되어 진행됨.
```js
// 스코프의 선두에서 선언 단계가 실행된다.
// 아직 변수가 초기화(메모리 공간 확보와 undefined로 초기화)되지 않았다.
// 따라서 변수 선언문 이전에 변수를 참조할 수 없다.

console.log(foo); // ReferenceError: foo is not defined

let foo; // 변수 선언문에서 초기화 단계가 실행된다.
console.log(foo); // undefined

foo = 1; // 할당문에서 할당 단계가 실행된다.
console.log(foo); // 1
```

변수 선언에는 기본적으로 ```const```를 사용하고, 재할당이 필요한 경우에 한정해 ```let```을 사용하는 것이 좋음. 그리고 객체를 재할당하는 경우는 생각보다 흔하지 않음. ```const```를 사용하면 의도치 않은 재할당을 방지해주기 때문에 보다 안전함.<p>
  1. 재할당이 필요한 경우에 한정해 ```let```를 사용함. 이떄, 변수의 스코프는 최대한 좁게 만듬
  2. 재할당이 필요 없는 상수와 객체에는 ```const```를 사용함.

<br>
<br>

## 지역변수 / 전역변수
지역변수는 블락 {}안에서 선언된 변수, 블락안에서만 쓸 수 있음.<p>
전역변수는 블락 밖에서 선언을 한 어디서든 쓰일 수 있는 변수<p>
```var```는 함수만 지역변수로 호이스팅이 되고, 나머지는 전부 전역변수로 올려버림.(for,if ...)