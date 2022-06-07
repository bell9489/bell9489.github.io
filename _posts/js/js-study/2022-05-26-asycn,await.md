---
layout: single
title: "async / await"
categories: [js-study]
tag: [js-study]
---

# Promise대신 ES8문법인 async, await을 이용해 Promise와 then을 대체해 보자.

<br>

**async**

1. 함수 앞에만 사용가능한 키워드다.
2. 함수 실행 후에 Promise 오브젝트가 남는다.
3. then을 사용할 수가 있다.

**await**

1. async function 안에서만 사용가능한 promise.then()의 대체문법이다.
2. promise를 기다린 다음에 완료되면 결과를 변수에 담는다.
3. 실패하면 에러가 나고 코드가 멈춘다.

<br>
<h5>콜백, promise, async, await 비교</h5>

```js
--------------------- 콜백함수 ---------------------
  function plus(callback){
    1 + 1;
    callback()
  }

  plus(x) // plus가 ① 소괄호안에 함수가 ②

--------------------- Promise ---------------------
  var a = new Promise(function (resolve, reject) {
    var plus = 1 + 1;
    resoleve(plus);
  });

  a.then(function (x) {
    console.log("good" + x);
  }).catch(function () {
    console.log("bad");
  });

--------------------- async ---------------------
  async function plus(){
    return 1 + 1; //return을 then파라미터를 사용하여 결과 확인이 가능.
  }

  plus().then(function(x){
    console.log(x)
  })

--------------------- await ---------------------
  async function plus(){
    var a = new Promise(function(resolve, reject){
      var b = 1 + 1;
      resolve();
    });

     var x = await a;
     console.log('good')
   }

    plsu();

// ▼ 실패를 다루는 방법

    try { var x = await a; }
    catch { a의 promise가 실패할 경우 실행될 코드}
```

<small>
async : return을 then파라미터를 사용하여 결과 확인이 가능하지만 성공한 결과만 확인 가능하다. <br>
await : 비동기식처리되는 코드를 담는다면 기다리는 동안 브라우저가 잠깐 멈출 수 있다.<br>
</small>

<br>
<h5>case.버튼을 누르면 콘솔창에 good 을 기다렸다가 띄우기</h5>

```js
var a = new Promise(function (resolve, reject) {
  document.getElementById("test").addEventListener("click", function () {
    resolve();
  });
});

async function btnPush() {
  var result = await a;
  console.log("good");
}

btnPush();
```
