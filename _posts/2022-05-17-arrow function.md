---
title: "[JS] arrow function"
excerpt: "ES6 신문법 화살표 함수에 대해서 확실히 이해를 해보자."

categories:
  - Javascript
tags:
  - [Javascript]

permalink: /javascript/arrow-function/

toc: true
toc_sticky: true

date: 2022-05-17
last_modified_at: 2022-06-08
---

**함수란**

1. 여러가지 기능을 하는 코드를 한 단어로 묶고 싶을 때 (재사용 할 때)
2. 입출력 기능을 만들 때

<br>

**arrow function 장점**

- 함수 본연의 기능을 잘 표현하는 문법이다.
- 파라미터 1개면 소괄호를 생략 할 수 있다.
- 코드 한줄이면 중괄호도 생략이 가능하다.
- 내부에서 this값을 쓸 때 밖에 있떤 this값을 그대로 사용한다.

<br>

**arrow function 예시**

1. 간단한 메소드 만들기

```js
var person = {
  name : 'Park',
}

person.sayHi();

// ▼ this 연습

var person = {
  name : 'Park',
  sayHi : funtion(){
    console.log('안녕 나는' + this.name)
  }
}

person.sayHi();
```

2. 오브젝트 내의 데이터를 전부 더해주는 메소드 만들기

```js
var x = {
  data: [1, 2, 3, 4, 5],
};

x.plus();

// ▼ this 연습

var x = {
  data: [1, 2, 3, 4, 5],
};

x.plus = function () {
  var sum = 0;
  this.data.forEach(function (a) {
    sum = sum + a;
  });
  console.log(sum);
};

x.plus();
```
