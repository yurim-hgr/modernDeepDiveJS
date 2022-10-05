# 33장 Symbol

## **1. Symbol**

**다른 값과 중복되지 않는 유일무이한 값**이다.

문자열과 같이 프로퍼티의 키값으로 사용할 수 있다.변경불가능한 원시값이다. ( 원시값이라서 `new`를 이용해서 생성하면 안됨 )

```
const symbol = Symbol("apple");
const copy = Symbol("apple");

// 유일무이한 값이기 때문에 같은 시드값을 넣어도 동일할 수 없음
console.log(symbol === copy);		// false

console.log(symbol.description);	// "apple"
console.log(symbol.toString());		// Symbol(apple)

// 문자열 or 숫자로 암묵적 변환 X
console.log(symbol + "");	// error
console.log(+symbol);		// error

// 불리언 암묵적 변환 O
console.log(!!symbol);		// true

// 전역 심벌 레지스트리에 값 저장 ( 없으면 생성 있으면 가져다 사용 )
const globalSymbol = Symbol.for("g");
const copySymbol = Symbol.for("g");
console.log(globalSymbol === copySymbol);	// true

// 전역 심벌 값의 키값 가져오기
Symbol.keyFor(globalSymbol);
```

- 타 언어의 `enum`처럼 활용가능함
- 프로퍼티로 만들면 기본적으로 은닉되며, `Object.getOwnPropertySymbols`로 찾을 수 있음

# 34장 이터러블

## 이터러블

이터러블 프로토콜을 준수한 객체를 이터러블이라 한다. 즉, 이터러블은Symbol.iterator를 프로퍼티 키로 사용한 메서드를 직접 구현하거나 프로토타입 체인을 통해 상속받은 객체를 말한다.

# 35장 스프레드문법

## 스프레드 문법

ES6에서 도입된 스프레드 문법(전개 문법) ...은 하나로 뭉쳐 있는 여러 값들의 집합을 펼쳐서(전개) 개별적인 값들의 목록으로 만든다.

스프레드 문법을 사용할 수 있는 대상은for ... of 문으로 순회할 수 있는 이터러블에 한정한다.

```jsx
스프레드 문법ES6에서 도입된 스프레드 문법(전개 문법) ...은 하나로 뭉쳐 있는 여러 값들의 집합을 펼쳐서(전개) 개별적인 값들의 목록으로 만든다.스프레드 문법을 사용할 수 있는 대상은for ... of 문으로 순회할 수 있는 이터러블에 한정한다.
//개별 요소로 분리한다.
console.log(...[1,2,3]); // 1 2 3

//문자열은 이터러블이다.
console.log(... 'Hello'); // H e l l o

//Map Set은 이터러블이다.
console.log(... new Map([['a','1'], ['b','2']])); // ['a', '1'] ['b', '2']
console.log(... new Set([1,2,3]));
// 1 2 3스프레드 문법의 결과물은 값으로 사용할 수 없고,쉼표로 구분한 값의 목록을 사용하는 문맥에서만 사용할 수 있다.

```

함수 호출문의 인수

- 목록배열
- 리터럴의 요소
- 목록객체
- 리터럴의 프로퍼티 목록

# 36장
