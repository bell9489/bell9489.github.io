---
title: "[React] useEffect"
excerpt: "Router로 페이지를 쪼개보자"

categories:
  - React
tags:
  - [React]

permalink: /react/useEffect/

toc: true
toc_sticky: true

date: 2022-06-29
last_modified_at: 2022-06-29
---

<!-- @format -->

## Lifecycle

- 컴포넌트는 인생을 만들수도 있고, 삭제도 할수 있고 관련 state를 재렌더링(업데이트)도 할 수 있다.
- 컴포넌트 중간중간 Hook(참견)을 할 수 있다.
- mount : 컴포넌트 등장 전에 할 일
- update : 컴포넌트 사라지기 전에 할 일
- unmount : 컴포넌트 업데이트 되고 나서 할 일

### 사용법

> <b>예전방식</b>
>
> 1.  class 컴포넌트 extends React.Component { 실행될 코드 }
>     componentDidMount(){} = 컴포넌트 첫 등장 후 실행할 코드
>     componentDidUpdate(){} = 컴포넌트 업데이트 할 때 코드
>     componentWillUnmount(){} = 다른페이지로 넘어가는 등의 컴포넌트 삭제 시 코드
>     <b>요즘방식</b>
> 2.  function 컴포넌트(){useEffect(()=>{ 실행될 코드 }); return()}
>     우선 페이지 상단에 useEffect를 import해야한다.
>     여러개 사용이 가능해서 useEffect(()=>{ 실행될 코드 }) 후에 한번더 사용하면 된다

```js
import React, { useEffect, useState } from "react";

function 컴포넌트() {
  useEffect(() => {
    // 첫번째로 실행될 코드
    });
  useEffect(() => {
    // 두번째로 실행될 코드
    });
  useEffect(() => { // 코드 살제하는 법
    return function xx(){ 실행할 코드 }
    });

    return (
      // html 실행할 코드
    )
  };
```

<br />

## useEffect

- Side Effect(함수의 핵심기능과 상관없는 부가기능) 이라 useEffect 라고 부른다.
- html 렌더링이 완료된 후에 실행이 된다 = 효율적이고 빠르게 활용이 된다.
- 어려운(시간이 오래걸리는) 연산을 사용한다.
- 서버에서 데이터를 가져 올때 사용한다.
- 타이머 장착시에 사용한다.

```js
// 컴포넌트 타이머에 맞혀서 사라지게 하기
function 컴포넌트() {
  useEffect(() => {
    let a = setTimeout(() => { // 타이머를 변수에 넣으면 타이머해제에 용이하다.
      setAlert(false);
    }, 2000);
    return () => {
      clearTimeout(a); // 기존 타이머 제거 // useEffect 실행전에 사용할 코드
    };
  }, []);

  let [alert, setAlert] = useState(true);

  return(
    {alert ? <div>사라지게 될 컴포넌트</div> : null}
  )};
```

<small>
- useEffect 실행조건 넣을 수 있는 곳은 [ ]이다. 즉, useEffect는 mount,update 될 떄마다 실행되는데 마지막에 실행이 될 곳을 지정해서 [ '실행시키고 싶은 state' ] 안에있는 state가 실행이 될때에만 useEffect가 실행된다. [] 안에 아무런 조건을 작성하지 않으면 컴포넌트 로드때만 한번 딱 실행 된다.<br />
- setTimeout을 사용하면 해제도 함꼐 해주어야 한다. 왜나하면 코드가 길어지거나 꼬이면 남아있는 타이머가 겹쳐지기 때문이다.<br />
- clean up function은 mount시에는 실행이 되지 않고 unmount = 삭제 될때만 실행된다.</small>
<br /><br />
