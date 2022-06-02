---
layout: single
title: "반복문 정리"
---

# for in, for of 반복문 / enumerable, iterable 속성

<br>

<mark>반복문의 종류</mark>

1. for : 어떤 특정한 조건이 거짓으로 판별될 때까지 반복.
2. forEach : array의 요소 또는 인덱스를 반환해주는 반복문.
3. for in : Object에 있는 key에 차례로 접근하는 데 사용되는 반복문.
4. for of : array의 객체를 하나씩 반환해주는 반복문.
5. while : 어떤 조건문이 참이기만 하면 문장을 계속해서 수행. 조건문이 거짓이 된다면, 그 반복문 안의 문장은 실행을 멈추고 반복문 바로 다음의 문장으로 넘어감.
6. do while : 특정한 조건이 거짓으로 판별될 때까지 반복.

**for in**

1. Object형에 있던 자료를 하나씩 추출할 때 사용된다.
2. 저장된 자료 갯수 많큼 반복된다.
3. enumerable(셀 수 있는지 여부 = 반복문에서 값을 출력할 것인지)한 것만 반복된다.
4. 부모의 prototype에 저장된 것도 출력한다는 단점이 있다.

<br>
<h5>for...in 사용법</h5>

```js
// 기본적인 사용법
var obj = { name: "kim", age: 20 };

for (var key in obj) {
  console.log(obj[key]);
}

// 부모의 prototype 대처법
class obj1 {}
obj1.prototype.name = "park";

var obj = new obj1();

for (var key in obj) {
  if (obj.hasOwnProperty(key)) {
    // 이 코드를 작성해야 부모 prototype이 안나온다.
    console.log(obj[key]);
  }
}
```

<br><br><br><br>

**for of**

1. array, string, arguments, NodeList, Map, Set 자료형에 적용할 수 있는 반복문이다.
2. iterable(내부 데이터 출력을 도와주는 함수 같은 것)만 반복된다.

<br>
<h5>for...of 사용법</h5>

```js
var arr = [2, 3, 4, 5];

for (var data of arr) {
  console.log(data);
}
```
