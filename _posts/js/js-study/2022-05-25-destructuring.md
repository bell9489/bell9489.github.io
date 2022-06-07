---
layout: single
title: "destructuring 문법으로 변수를 쉽게 만들어 보자"
categories: [js-study]
tag: [js-study]
---

# 자료형 변수를 뽑는 destructuring

<br>

**destructuring 문법**

1. array, object에 있는 자료들을 변수로 변경이 가능하다.
2. pattern maching 이라고도 불리운다.
3. 모양을 맞춰 등호를 이용해서 좌우를 똑같이 만들어 주면 된다.

<br>
<h5>Array 자료를 변수로 변경하는 법</h5>

```js
var array = [2, 3, 4];
var a = arr[0];
var b = arr[1];

// ▼ 밑에방법으로 가능
var [a, b, c] = [2, 3, 4];

// ▼ 기본값도 가능
var [a, b, c] = [2, 3]; // 값이 할당이 안되면 undefined가 할당된다.
var [a, b, c = 5] = [2, 3]; // default값으로 c는 5가 출력된다.
```

<small>왼쪽과 오른쪽의 갯수를 동일하게 사용하며 위치를 동일하게 배치한다.</small>

<br>
<h5>Object 자료를 변수로 변경하는 법</h5>

```js
var obj = { name: "kim", age: 30 };
var name = obj.name;
var age = obj.age;

// ▼ 밑에방법으로 가능
var { name, age } = { name: "kim", age: 30 };

// ▼ 기본값도 가능
var { name, age = 40 } = { name: "kim" };

// ▼ 변수명도 가능
var { name: nickname, age = 40 } = { name: "kim" }; // nickname을 입력하면 'kim'이 출력된다.

// ▼ 변수명에 기본값도 가능
var { name: nickname = oreo } = {}; // nickname을 입력하면 'oreo'가 출력된다.
```

<small>키값을 동일하게 작성해야 한다.</small>

<br>
<h5>변수들을 object에 넣는 법</h5>

```js
var name = "kim";
var age = 30;

var obj = { name: name, age: age };

// ▼ 밑에방법으로 가능
var obj = { name, age }; //key와 value 값이 같을 때 가능하다
```

<br>
<h5>함수 파라미터에 변수를 생성 하는 법</h5>

```js
var obj = { name: "kim", age: 30 };

function x({ name, age }) {
  console.log(name);
  console.log(age);
}

x({ name: "kim", age: 30 }); // kim과 30이 각각 출력된다.
```

<small>파라미터는 변수랑 똑같다.</small>
