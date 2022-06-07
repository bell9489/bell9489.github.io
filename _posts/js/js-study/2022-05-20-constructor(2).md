---
layout: single
title: "자바스크립트 속 상속 기능들 ES5/ES6"
categories: [js-study]
tag: [js-study]
---

# 상속기능을 구현한 ES5 방법

<br>

**Object.create(prototype object);**

1. ES5 출시 때 나온 문법으로 상속기능을 한다.
2. 상속을 이용해서 오브젝트를 만들고 싶을 때 편리하지만 class 문법에 밀려 인지도가 낮다.

<br>

```js
var x = { name: "kim", age: 40 };
var y = Object.create(x);

console.log(age); // 40이 출력된다.
```

<small>사용법 : Object.create(상속받고 싶은 object)를 사용하면 된다.</small>

<h5>상속받은 object에서 값 하나만 변경하고 싶을 때</h5>

```js
var x = { name: "kim", age: 40 };
var y = Object.create(x);
y.age = 20;

var z = Object.create(y);

console.log(y.age); // 20이 출력된다.
console.log(z.age); // 20이 출력된다.
```

<small>자바스크립트 오브젝트 자료형에서 특정 자료를 꺼낼 때는 순서가 있다.<br>

1. 자식의 object에 값을 직접 가지고 있을 때 출력
2. 없으면 자식의 부모 prototype에 값이 있으면 그 값을 출력
3. 부모도 없으면 부모의 부모의 prototype을 확인하여 그 값을 출력</small>
