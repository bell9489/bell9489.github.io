---
title: "[React] Component"
excerpt: "복잡한 html을 한 단어로 치환하는 component"

categories:
  - React
tags:
  - [React]

permalink: /react/component/

toc: true
toc_sticky: true

date: 2022-06-13
last_modified_at: 2022-06-13
---

<!-- @format -->

## component 란

- 리액트상에서 긴 html을 한 단어로 치환해서 넣을 수 있는 문법

### 사용법

> 1.  function을 사용해 함수를 만들어 작명
> 2.  함수 안에 return ( <b>원하는 html</b> )
> 3.  필요한 곳에 <b><함수명></함수명></b> 사용

<br />

### 주의점

- component를 작명할 때 시작은 영어대문자
- return () 안엔 html 태그들이 평행하게 넣을 수 없다.
  - 굳이 평행하게 넣고 싶으면 <b><> 넣고싶은 코드 </></b> ▸ fragment 문법
- function App(){} 도 컴포넌트 생성문법이라 App 외부에 생성
  - component 안에 component를 만들지 않는다.

<br />

### component로 만들면 좋은 것들

<br />

- 반복 횟수가 잦은 것
- 내용이 자주 변경 될 것 같은 html 부분만 component로 만들기
- 다른 페이지를 만들 때
- 다른 팀원과 협업할 때 웹페이지를 component 단위로 나눠서 작업할 때
- 함수 문법과 똑같다고 생각하면 된다.

<br />

### component 단점

<br />

- component 가 많으면 관리가 힘들다
- 한 function 안에 있는 변수를 다른 function에서 맘대로 사용이 불가해 props를 사용해야하는데 번거롭다.

```js
function App() {
  return (
    <div>
      <modal />
    </div>
  );
}

function Modal() {
  return (
    <div className='modal'>
      <h4>제목</h4>
      <p>날짜</p>
      <p>기간</p>
    </div>
  );
}
```

<br /><br />
