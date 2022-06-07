---
title: "[JS] constructor"
excerpt: "자바스크립트 속 상속 기능들"

categories:
  - Javascript
tags:
  - [Javascript]

permalink: /javascript/constructor/

toc: true
toc_sticky: true

date: 2022-05-20
last_modified_at: 2022-06-08
---

**constructor**

1. object 자료 복사할 때 함수로 생성한다.
2. 비슷하고 독립적인 object 자료를 여러개 간단하게 만들 수 있다.

<br>

```js
function x() {
  this.morning = "apple";
  this.time = 09;
}

var menu1 = new x(); // menu1을 출력하면 x의 오브젝트 값이 나온다.
var menu2 = new x(); // menu2를 출력하면 x의 오브젝트 값이 나온다.
```

<small>사용법 : 새로운 함수 오브젝트를 생성한 뒤에 new라는 키워드를 사용하여 오른쪽에 constructor 이름을 쓰면 새로운 오브젝트를 생성할 수 있다. 그런뒤에 그걸 변수에 저장하면 자유롭게 오브젝트 사용이 가능하다.</small>

<br>

<h5>오브젝트 속 함수</h5>

```js
function x(a, b) {
  this.morning = a;
  this.time = b;
  this.guide = function () {
    console.log("아침 메뉴는" + this.morning + "입니다");
  };
}

var menu1 = new x("apple", 09); // a, b 순서대로 원하는 값 넣기
var menu2 = new x("bread", 10); // a, b 순서대로 원하는 값 넣기
```

<small>
함수 속 파라미터를 통해 값 변경이 자유롭다.
</small>

<br><br><br><br>

# 2. prototype

<br>

**prototype**

1. 상속을 구현 할 수 있는 자바스크립트만의 문법
2. constructor(함수)를 만들면 prototype 이라는 공간이 자동적으로 생성된다.
3. object 자료형 처럼 값을 여러개도 가능하며 함수도 가능하다.
4. 부모에 값을 등록하여 모든 자식이 사용 가능하끔 하는 유전자라고 쉽게 정의가 가능하다.
5. 추가된 데이터들은 자식들이 가지고 있는게 아닌 부모만 가지고 있는 값이다.

<br>

```js
function x() {
  this.morning = "bread";
  this.time = 09;
}

x.prototype.drink = "coffee";

var menu1 = new x(); // menu1.drink 를 출력하면 coffee 가 나온다.
```

<br>

<h5>자바스크립트 내장합수가 사용 가능한 이유</h5>

- 자바스크립트에는 array, object에 붙일 수 있는 내장함수들 (sort, push, toString, map, for Each 등등)이 있는데 이유는 **내가 만든 array, object의 부모 유전자가 내장함수를 가지고 있기 때문이다.**

<br>

```js
var arr = [1, 2, 3]; // 이렇게 사람이 작성하면
var arr = new Array(1, 2, 3); // 이렇게 컴퓨터에 저장 된다.
```

- 위의 두개의 코드는 같은 의미이다. newArray는 기계로부터 자식을 하나 새로 생성해 달라는 의미 이다.

```js
console.log(Array.prototype); // 추력하면 sort, map, push, forEach 등등이 등장한다.
```

- 그래서 위의 출력값처럼 부모의 prototype 이 가지고 있는 내장함수를 가져다 쓸수 있는 것이다.

<br>

<h3><mark>prototype의 상속 vs constructor 상속</mark></h3>

- 자식들이 값을 직접 가지고 있게 하고 싶으면 constructor
- 부모만 값을 가지고 자식은 그걸 참조해서 쓰려면 prototype
