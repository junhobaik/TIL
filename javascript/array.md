# JavaScript Array
#### 배열

자바스크립트의 배열은 어떤 타입이던 담을 수 있고, 배열 크기도 미리 정하지 않는다.

```javascript
var arr = [
  null,
  undefined,
  true,
  1,
  "array",
  {}
];

console.log(arr); 
// [null, undefined, true, 1, "array", [object Object]{...}]

console.log(typeof arr, toString.call(arr));
//'object', '[object Array]'
```



- 배열에서 빈 슬롯의 주의점

배열에서 주의 해야할 점은 중간에 빈 구멍이 있는 배열을 조심해야 한다.

```javascript
var arr = [];
arr[0] = 1;
arr[2] = 2;
arr[3] = undefined;
```

위와 같은 코드가 있을때 배열의 1번은 비어있을 것이다. 어떤 배열이 되어있을지 보면

```javascript
console.log(arr); //[1, undefined, 2, undefined]
console.log(arr.length); // 4
```

위와 같이 되어있다. 비어있는 배열이 undefined가 되어있다.
1번 undefined와 따로 선언한 undefined의 3번은 서로 같은 것인 것일까?

```javascript
console.log(arr[1] === arr[3])
console.log(typeof arr[1] === typeof arr[3]);
console.log(toString.call(arr[1]) === toString.call(arr[3]));
console.log(arr[1] === undefined);
console.log(arr[3] === undefined);
```

이렇게 비교를 해 보아도 모두가 **true** 로 일치한다고 나온다 하지만
빈 슬롯이 undefined과 된 것과 선언으로 인해 undefined 인 것은 **엄연히 다르다.**

그 이유는 아래에서 알 수 있다.

```javascript
console.log(arr);
[1, undefined, 2, undefined]

for(index in arr){
  console.log(index);
}
// 0, 2, 3

var newArr = [];
arr.forEach(function(value, index){
  console.log("index:"+index+"/value:"+value);
  newArr.push(value);
})
// "index:0/value:1"
// "index:2/value:2"
// "index:3/value:undefined"

console.log(newArr);
// [1, 2, undefined]
```

for in, forEach 등을 통해 실험을 해 본 결과이다.
for in 에서는 index 1이 존재하지 않는 것으로 보이고,
forEach를 통해서도 새로운 배열을 복사하는 것을 하려 했으나 1번 배열이 빠진채로 수행 된 것을 볼 수 있다.

이러한 예제를 통해 빈 슬롯이 있는 배열을 다루게 된다면 조심해야한다는 것을 알 수 있다.



- 배열의 key/property 형태의 활용

배열 인덱스는 숫자이다. 그런데 배열도 객체이기 때문에 key/property 문자열을 추가 할 수 있다.

```javascript
var arr = [];

arr[0] = 1;
arr["two"] = 2;
```

조심해야할 점은 이렇게 선언할 경우 배열의 길이는 늘어나지 않는 것을 조심해야한다. 또한 배열을 출력할 경우 나타나지 않는다.

```javascript
console.log(arr); // [1]
console.log(arr["two"]); // 2

console.log(arr.length); // 1

for(index in arr){
  console.log(index);
} // '0'
```

더욱 조심해야 할 점은 키로 넣은 문자열이 표준 10진수 숫자로 이루어져 있다면 아래와 같은 결과를 얻게 된다.

```javascript
arr["5"] = "five";
console.log(arr);
//[1, undefined, undefined, undefined, undefined, "five"]
console.log(arr.length); // 6

for(index in arr){
  console.log(index);
} // '0', '5', 'two'
```

키/프로퍼티 형태로 활용하는 것을 지양하고 이렇게 써야한다는 상황이라면 문자열 프로퍼티는 꼭 숫자가 아닌 글자만 사용하도록 하자.



- 유사배열

유사배열을 진짜 배열로 바꾸는 방법

일반적으로 indexOf, concat, forEach 등의 배열 함수들을 사용한다, 
또한 slice를 활용한 방법도 있다

```javascript
function test(){
  var arr = Array.prototype.slice.call( arguments );
  return arr;
}

var a = test('a', 1);
console.log(toString.call(a), a); 
//"[object Array]" ["a", 1]
```

ES6에 와서는 유사 배열을 진짜 배열로 바꾸는 기능이 추가되었다. 
`Array.from()`

```javascript
function test(){
  var arr = Array.from( arguments );
  return arr;
}

var a = test('a', 1);
console.log(toString.call(a), a); 
//"[object Array]" ["a", 1]
```