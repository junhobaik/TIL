# Javascript Variable Types



자바스크립트의 변수는 모든 데이터 타입을 수용할 수 있도록 되어있다.

`typeof` 라는 특정 변수의 데이터 타입을 확인하여 문자열로 반환하는 연산자가 있다.



#### Standard defines seven data types
1. Six data types that are primitives
  1. Boolean
  2. Null
  3. Undefinend
  4. Number
  5. String
  6. Symbol
2. and Object




#### typeof results


| Type             | 'typeof' Result |
| ---------------- | --------------- |
| number           | number          |
| string           | string          |
| boolean          | boolean         |
| undefined        | undefined       |
| null             | **object**      |
| symbol           | symbol          |
| function object  | function        |
| any other object | object          |



- **typeof null === 'object' //… true ??**

자바스크립트에서는 null 이 기본형으로 구분되어있다.
하지만 typeof null의 결과로는 null이 반환되지 않고 object가 반환되는 이유는 자바스크립트 개발 당시 다른 언어들과 같이 null이 0값을 가지고 있는 객체로 취급하여 object를 반환하도록 개발되었기 때문이다.
null값이 기본형이므로 반환값을 null로 바꾸자는 의견도 많으나 이미 object 반환 방식으로 구현된 웹들이 많아 쉽게 바꾸지 못하고 있다.
