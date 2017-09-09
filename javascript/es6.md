# ES6 (ES2015)



사실상 최신 자바스크립트 표준이다.
ES6를 기반으로 한 라이브러리 등 자바스크립트 생태계가 변화, 이미 많이 변화되었다.



#### ES6 호환성 표
[ECMAScript 6 compatibility table](https://kangax.github.io/compat-table/)
Chrome 브라우저에서 95% 이상으로 높은 호환성을 보이고 있다.

ES6 환경으로 구현 후 Babel을 이용 ES6로 변환하여 사용하면 호환성 문제를 해결,
현재 대부분의 브라우저 환경에서 사용가능하도록 할 수 있다.



---



선택되지 않은 사항은 정리할 내용이 많아 레포지토리 내에 따로 문서로 작성되어있는 것들.

선택된 사항은 다소 내용이 작아 해당 문서 아래에 작성되어있다.



- [ ] const / let
- [ ] String methods
   1. startsWith()
   2. endsWith()
   3. includes()
- [ ] for of 
- [ ] Spread Operator
- [ ] from
- [x] <a href="#1">간단히 객체 생성하기</a>
- [x] <a href="#2">Destructuring Array</a>


- [x] <a href="#3">Destructuring Object</a>
- [ ] Set, WeakSet / Map, WeakMap
- [x] <a href="#4">Template</a>
- [x] <a href="#5">Tagged Template Literals</a>
- [ ] Arrow Function
- [x] <a href="#6">Function default paramater</a>
- [x] <a href="#7">Rest paramater</a>
- [ ] Class
- [ ] Object assign
- [ ] setPrototypeOf
- [ ] module
- [ ] proxy




---



<a name="1"/>

### 간단히 객체 생성하기

```javascript
const name = 'baik';
const age = '27';

const jsonObj = {
  name : name
  age : age
}

const newJsonObj = {
  name,
  age
}
```



<a name="2"/>

### Destructuring Array

```javascript
let data = ['A','B','C'];

let b = data[1];

let [a, ,c] = data;

console.log(a); // "A"
console.log(c); // "C"
```



<a name="3"/>

### Destructuring Object

```javascript
let obj = {
  name : 'baik',
  age : 27
}

let { name, age } = obj;
console.log(name, age);
// "baik" 27

let { name:myName, age:myAge } = obj;
console.log(myName, myAge);
// "baik" 27

/**************/

document.querySelector('div').addEventListener("Click", function(event){
  console.log(event.target.tagName)
});

document.querySelector('div').addEventListener("Click", function( { target } ){
  console.log(target.tagName)
});
```



<a name="4"/>

 ### Template 처리

```javascript
const data = [{}]; //json data...

const template = `<div> hi ${data[0].name} </div>`;
```

<a name="5"/>

### Tagged Template Literals

```javascript
const data = [
  {
    name:'baik',
    age:27
  },
  {
    name:'kim',
    age:17
  }
];


function fn(tags, name, age, msg){
  if(age < 20){
    msg = "미성년자입니다"
  }else{ 
    msg = "성인입니다"; 
  }
  
  return (tags[0] + name + tags[1] + age + tags[2] + msg + tags[3]);
}

data.forEach((v)=>{
  let template = fn`<div>hi ${v.name}, age:${v.age}, ${v.msg}</div>`;
  console.log(template);
});

```



<a name="6"/>

### Function default paramater

```javascript
function sum(a, b){
  b = b || 1; // b인자가 없을때 기본값 지정
  return a + b;
}

function es6_sum(a, b=1){ //파라메터에 기본 값 지정
  return a + b;
}

console.log(sum(1));
console.log(es6_sum(1));
```



<a name="7"/>

### Rest paramaters

```javascript
function checkString() {
  let arg = Array.from(arguments);
  const result = arg.every((v) => typeof v === "string");
  console.log(result);
}

function es6_checkString(...arg) { //rest paramater
  const result = arg.every((v) => typeof v === "string");
  console.log(result);
}

checkString(1,2,"3");
checkString("1","2","3");

es6_checkString(1,2,"3");
es6_checkString("1","2","3");
```



---

## reference

- [모던 자바스크립트(javascript) 개발을 위한 ES6 강좌](https://www.inflearn.com/course/es6-%ea%b0%95%ec%a2%8c-%ec%9e%90%eb%b0%94%ec%8a%a4%ed%81%ac%eb%a6%bd%ed%8a%b8/)