---
title: "[React] 간단한 todoList(1)"
excerpt: "간단하게 만드는 todoList로 리액트에 전반을 이해해보자"

categories:
  - React
tags:
  - [React]

permalink: /react/todo-simple/

toc: true
toc_sticky: true

date: 2022-06-09
last_modified_at: 2022-06-09
---

## 구현할 기능

> - ToDo List의 메인
> - ToDo Item
> - ToDo Item을 추가하면 ToDo List의 추가되는 기능
> - 삭제 버튼을 누르면 삭제되는 기능

<center>
  <img src="https://user-images.githubusercontent.com/93906032/172792344-0b64558b-bcb2-4452-9665-72f75f392680.jpg" width="500"/>
</center> <br />

## 개발할 페이지와 컴포넌트

- Home : 첫 화면 ▸ ToDo List를 보여준다
- Components ▸ 입력을 하는 컴포넌트 / 리스트 컴포넌트 / 아이템 컴포넌트

<br /><br />

<center><b>디렉토리 구조</b></center><br />

<center>
  <img src="https://user-images.githubusercontent.com/93906032/172792535-921fb2a9-1b4a-4afd-a6f6-44a910784ce1.jpg" width="300"/>
</center> <br />

## 구현할 기능

### ToDo List메인에 input과 button을 만든다.

```js
import React from "react";

export default function App() {
  return (
    <div className="App">
      <input type="text" />
      <button>추가</button>
    </div>
  );
}
```

<br />

### `input`창에 값을 적는대로 표기하고 값을 저장을 해 놨다가 아이템으로 전달하는 함수를 적용한다.

```js
  <input type = "text" onChange={(event)=>(event.target.value)}/>
  <button>추가</button>
```

<br />

### `input`창에 아이템을 저장할 state를 작성해서 value값을 할당한다.

```js
<input type="text" onChange={(event) => setValue(event.target.value)} value={value} />
```

<br />

### `button`을 클릭하면 호출될 함수 작성 - 아이템을 추가 해 할일들을 모아둘 배열의 state를 만든다.

```js
import { useState } from "react";

export default function App() {
  const [value, setValue] = useState("");
  const [toDoList, setToDolist] = useState([]); //input에서 받아온 값을 배열로 정리
  const item = () => {
    setToDolist([...toDoList, value]); //배열들을 풀어서 변하는 값을 저장
  };

  return (
    <div className="App">
      <input type="text" onChange={(event) => setValue(event.target.value)} value={value} />
      <button onClick={item}>추가</button>
    </div>
  );
}
```

<small>값 추가를 setTodoList에 업데이트를 하는데 기존의 아이템은 유지를 하고 뒤에 새로운 inputValue를 넣어준다</small>
<br />

### item component와 item들을 모은 bord component 만들기

```js
//ToDoItem

import React from "react";

function ToDoItem() {
  return <div>첫번째 할일</div>;
}

export default ToDoItem;

//ToDoBoard

import React from "react";
import ToDoItem from "./ToDoItem";

function ToDoBoard() {
  return (
    <div>
      <h1>ToDo List</h1>
      <ToDoItem />
    </div>
  );
}

export default ToDoBoard;
```

<br />
<center><b>지금까지의 결과</b></center>

<center>
  <img src="https://user-images.githubusercontent.com/93906032/172792621-b8aed8a4-0630-4370-ab03-3de187c0639a.jpg" width="400"/>
</center> <br />

### ToDoBoard와 ToDoItem에 props 사용

- todoList에 보여줄 정보는 todoList 배열에 있는 아이템인데 todoList가 가지고 있는 파일 App.js에서 정보를 보여줘야할 파일은 ToDoBoard이기에 <mark>props</mark>를 사용하여 파일을 전달받는다.

```js
//ToDoBoard

import React from "react";
import ToDoItem from "./ToDoItem";

function ToDoBoard(props) {
  return (
    <div>
      <h1>ToDo List</h1>
      {props.toDoList.map((item) => (
        <ToDoItem item={item} />
      ))}
    </div>
  );
}

export default ToDoBoard;
```

<small>map함수를 통해 배열을 추출을 한다.</small>
<br /><br />

```js
//ToDoItem

import React from "react";

function ToDoItem(props) {
  return <div>{props.item}</div>;
}

export default ToDoItem;
```

<small>item들을 전달받아 추가한다.</small>
<br /><br />

### ToDoBoard에 보여질 toDoList를 작성한다.

```js
<ToDoBoard toDoList={toDoList} />
```

## 최종 코드

```js
// App.js

import { useState } from "react";
import ToDoBoard from "./compontents/ToDoBoard";

export default function App() {
  const [value, setValue] = useState("");
  const [toDoList, setToDolist] = useState([]);
  const item = () => {
    setToDolist([...toDoList, value]);
  };

  return (
    <div className="App">
      <input
        type="text"
        onChange={(event) => setValue(event.target.value)}
        value={value}
      />
      <button onClick={item}>추가</button>

      <ToDoBoard toDoList={toDoList} />
    </div>
  );
}


// ToDoBoard

import React from "react";
import ToDoItem from "./ToDoItem";

function ToDoBoard(props) {
  return (
    <div>
      <h1>ToDo List</h1>
      {props.toDoList.map((item) => (
        <ToDoItem item={item} />
      ))}
    </div>
  );
}

export default ToDoBoard;


// ToDoItem

import React from "react";

function ToDoItem(props) {
  return <div>{props.item}</div>;
}

export default ToDoItem;
```

<br />
<center><b>지금까지의 결과</b></center>

<p align="center"><img src="https://user-images.githubusercontent.com/93906032/172784766-94679477-f653-4167-8eba-60fda3b5efe9.gif"></p>
