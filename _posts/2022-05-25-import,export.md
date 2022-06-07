---
title: "[JS] import / export"
excerpt: "import / export를 이용한 파일간 모듈식 개발"

categories:
  - Javascript
tags:
  - [Javascript]

permalink: /javascript/import-export/

toc: true
toc_sticky: true

date: 2022-05-25
last_modified_at: 2022-06-08
---

**import**

1. 변수명은 작명이 가능하다.
2. 변수, 함수는 사용은 가능하지만 수정은 불가능하다. read-only 이다.

**export**

2. export default 는 파일당 1회만 사용이 가능하다.
3. 변수, 함수 선언 왼쪽에 작성해도 가능하다. <mark>export var 변수 = 99;</mark>

<br>
<h5>html파일에서 ES6 import 문법을 사용하려면</h5>

```js
<script type="module">import a from '/xxx.js'</script>
```

<small>
일반 프론트엔드 개발시에는 script src="/xxx.js"을 작성하는게 최고이다.
</small>

<br>
<h5>export default / import</h5>

```js
--------- export 파일 ---------

      var a = 10;
      export default a;

--------- import 파일 ---------

      import a from '/library.js'
```

<small>
<b>export</b> : export default 변수명<br>
<b>import</b> : import 변수명 from '경로'
</small>

<br><br>

<h5>export의 가짓수</h5>

```js
--------- export 파일 ---------

      var a = 10;
      var b = 20;
      export {a, b};

--------- import 파일 ---------

      import {a,b} from '/library.js'
```

<small>
<b>export</b> : export {변수1,변수2};<br>
<b>import</b> : import {변수1,변수2} from '경로'
</small>

<br><br>

<h5>export와 export default가 공존 할 때</h5>

```js
--------- export 파일 ---------

      var a = 10;
      var b = 20;
      var c = 30;
      export {a, b};
      export default c;

--------- import 파일 ---------

      import c, {a,b} from '/library.js'
```

<small>
<b>export</b> : export {변수1,변수2}; export default 변수3;<br>
<b>import</b> : import 변수3, {변수1,변수2} from '경로'
</small>

<br><br>

<h5>import에서 변수명 변경 법 <mark>as</mark></h5>

```js
--------- export 파일 ---------

      var a = 10;
      var b = 20;
      export {a};
      export default b;

--------- import 파일 ---------

      import b as bbbbb {a as aaaa} from '/library.js'
```

<small>
<b>export</b> : export {변수1}; export default 변수2;<br>
<b>import</b> : import 변수2 as 변수2변경, {변수1 as 변수1변경} from '경로'
</small>

<br><br>

<h5>import할 변수가 많을 때 <mark>*</mark></h5>

```js
--------- export 파일 ---------

      var a = 10;
      var b = 20;
      var c = 30;
      export {a,b};
      export default c;

--------- import 파일 ---------

      import c, {* as 변수모음} from '/library.js';
      console.log(변수모음.a);
      console.log(c);
```

<small>
<b>import</b> : as로 별명을 지어주어야 한다. 그래야 별명에 export 했던 변수들이 들어간다. (export default 했던 변수는 기존대로 import 하면 된다.)
</small>
