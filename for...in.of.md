## for...in
문법
>**for** (variable **in** object) { ... }

- variable: 속성 이름을 변수로 지정하기
- object: 반복작업을 수행할 객체. 열거형 속성을 가지고 있는 객체

for...in은 array(배열)에서 반복할 수 없다. 객체 반복에 사용

for...in을 사용하는 이유: 특정 값을 가진 키가 있는지 확인하려는 경우에 사용할 수 있다. 콘솔이나 다른 방법으로 객체의 속성을 확인할 수 있기 때문에 디버깅을 위해 사용될 수 있다.
<for in 반복문 예시>
```
const object = { a: 1, b: 2, c: 3 };

for (const property in object) {
  console.log(`${property}: ${object[property]}`);
}

// "a: 1"
// "b: 2"
// "c: 3"

```


## for...of


문법
>for (variable of iterable) {
	statement
    }
    
- variable: 각 반복에 서로 다른 속성값이 variable에 할당된다.
- iterable: 반복되는 열거가능(enumerable)한 속성이 있는 객체.

이터러블: 이터러블 프로토콜을 준수한 객체(ex.Array, String, Map, Set, TypedArray, arguments 등)
이터러블은 for...of문으로 순회할 수 있다.

<Map에 대한 for...of 반복문 예시>

```
let iterable = new Map([["a", 1], ["b", 2], ["c", 3]]);

for (let entry of iterable) {
  console.log(entry);
}
// [a, 1]
// [b, 2]
// [c, 3]

for (let [key, value] of iterable) {
  console.log(value);
}
// 1
// 2
// 3
```

출처: https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...in 를 참고하였습니다.


