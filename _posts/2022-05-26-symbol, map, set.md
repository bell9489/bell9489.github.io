---
title: "[JS] symbol / map / set"
excerpt: "잘 쓰이지는 않지만 알아두면 좋은 자료형들."

categories:
  - Javascript
tags:
  - [Javascript]

permalink: /javascript/symbol-map-set/

toc: true
toc_sticky: true

date: 2022-05-26
last_modified_at: 2022-06-08
---

**Symbol**

1. Object에 설명을 비밀스럽게 저장할 수 있는 자료형.
2. for문에 등장하지 않는다.
3. 같은 설명을 적었다고 두개의 boolean이 같아지는 것이 아니다.
4. Symbol.for() 를 작성하면 변수취급이 가능해서 boolean이 같아질 수 있다.

<br>
<h5>Symbol 사용법</h5>

```js
// ▼ 기본적인 방법 ①
var a = Symbol("very very good");

// ▼ 기본적인 방법 ② - Object 안에 직접 입력하는
var a = Symbol("very very good");
var b = { name: "kim", [age]: 20 };

// ▼ Object에 비밀스러운 key값 부여
var a = { name: "kim" };
a.age = 100;

var age = Symbol("secret");
a[age] = 999;

console.log(a);
```

<br><br><br><br>

**Map**

1. Object자료형과 같이 key, value 형태로 자료를 저장할 수 있는 자료형이다.
2. 자료들간의 연관성을 표현하기 위해 쓰인다.
3. key, value 형식으로 저장하려면 Object를 사용하고 key, value가 관련 있다는걸 저장할 때 Map을 쓴다.

<br>
<h5>Map 사용법</h5>

```js
// ▼ 기본적인 방법
var person = new Map();
person.set("name", "kim");
person.set("age", 20);

// ▼ 다루는 법
var person = new Map();
person.set("age", 20);

person.get("age"); // 자료 꺼내는 법
person.delete("age"); // 자료 삭제하는 법
person.size; // 자료 갯수 세는 법

// ▼ 반복문 돌리는 법
for (var key of person.keys()) {
  console.log(key);
}

// ▼ 자료를 직접 넣는 법
var person = new Map([
  ["age", 20],
  ["name", "kim"],
]);
```

<br><br><br><br>

**Set**

1. 간단한 Array 자료형과 똑같이 생겼다. (자료를 일렬로 쭉 저장할 수 있다.)
2. Array 이지만 중괄호로 표현이 된다.
3. 중복자료를 절대 허용하지 않는다. (중복 데이터를 방지하고 싶을 때 사용한다.)
4. Array 데이터 중복제거할 때 많이 사용된다.

<br>
<h5>Set 사용법</h5>

```js
// ▼ 기본적인 방법
var a = new Set(["kim", "park", "lee"]);

console.log(a);

// ▼ 다루는 법
var a = new Set(["kim", "park", "lee"]);

a.add("jung"); // 자료 더하는 법
a.has("kim"); // 자료 확인하는 법
a.size; // 자료 갯수 세는 법

// ▼ Array에 있는 중복데이터 제거하는 법
var a = ["kim", "park", "lee"];
var b = new Set(a); // Array를 Set으로 바꾸기

a = [...b]; //Set을 Array로 바꾸기
```
