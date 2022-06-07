---
title: "[JS] apply / call"
excerpt: "apply과 call의 차이점"

categories:
  - Javascript
tags:
  - [Javascript]

permalink: /javascript/apply-call/

toc: true
toc_sticky: true

date: 2022-05-18
last_modified_at: 2022-06-08
---

**apply**

1. 함수를 호출하는 기능
2. this로 사용할 객체를 전달하면서 함수를 호출한다.
3. 호출할 함수의 인수를 배열로 묶어 전달한다. = 파라미터를 <mark>[array]</mark>로 한꺼번에 집어넣을 수 있다.

<br>

```js
var person = {
  x: function () {
    console.log(this.name + "hi");
  },
};

var person2 = {
  name: "kim",
};

person.x.apply(person2); // [1,2,3 으로 출력된다.]
```

<small>사용법 : 실행할함수.apply(적용할곳);</small>

<br>

**call**

1. 함수를 호출하는 기능
2. this로 사용할 객체를 전달하면서 함수를 호출한다.
3. 파라미터를 <mark>1,2,3 이렇게 일반 함수처럼</mark>로 집어넣을 수 있다.

<br>

```js
var person = {
  x: function () {
    console.log(this.name + "hi");
  },
};

var person2 = {
  name: "kim",
};

person.x.call(person2); // (1,2,3 으로 출력된다.)
```

<small>사용법 : 실행할함수.call(적용할곳);</small>

<br>
