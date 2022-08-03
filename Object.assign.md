Object.assign() 메서드는 출처 객체들의 모든 열거 가능한 자체 속성을 복사해 대상 객체에 붙여넣습니다. 그 후 대상 객체를 반환합니다.

> Object.assign([target 객체],[여러개의 객체])
> 
- target 객체: 목표 객체. 출처 객체의 속성을 받아 반영된 목표 객체를 반환합니다.
- 여러개의 객체: 목표 객체에 반영하고자 하는 속성들을 갖고 있는 객체입니다.

예시 1 객체와 객체 병합

```
const apple = {a: 1, b: 2};
const banana = {b: 3, c: 4};

const return = Object.assign(apple, banana);

console.log(apple);
 // 결과값: {a: 1, b: 3, c: 4}
console.log(target);
 // 결과값: {a: 1, b: 3, c: 4}

```

예시 2 빈 객체와 배열 병합

```
const array = ['first', 'second', 'third'];
const obj = Object.assign({}, array);
console.log(obj);
 // 결과값: {'0': 'first', '1': 'second', '2': 'third'}
console.log(array);
 // 결과값: ['first', 'second', 'third']

```

예시 3 같은 속성을 가진 객체 병합

```
const o1 = { a: 1, b: 1, c: 1 };
const o2 = { b: 2, c: 2 };
const o3 = { c: 3 };

const obj = Object.assign({}, o1, o2, o3);

console.log(obj);
 // 결과값: { a: 1, b: 2, c: 3 }

```

출처: [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/assign](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) 을 참고하였습니다.
