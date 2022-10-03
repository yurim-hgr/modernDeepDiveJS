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
