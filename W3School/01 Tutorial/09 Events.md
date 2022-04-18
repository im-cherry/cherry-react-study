# 09 Events

HTML DOM 이벤트처럼 React는 사용자 이벤트를 기반으로 작업을 수행할 수 있습니다.

<br/>

## 1. Adding Events

React 이벤트는 camelCase 구문으로 작성합니다.  
React 이벤트 핸들러는 중괄호 안에 작성합니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Football() {
  const shoot = () => {
    alert("Great Shot!");
  };

  return <button onClick={shoot}>Take the shot!</button>;
}

ReactDOM.render(<Football />, document.getElementById("root"));
```

<br/>
<br/>

## 2. Passing Arguments

Arrow Function을 사용하여 이벤트 핸들러에 인자를 전달합니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Football() {
  const shoot = (a) => {
    alert(a);
  };

  return <button onClick={() => shoot("Goal!")}>Take the shot!</button>;
}

ReactDOM.render(<Football />, document.getElementById("root"));
```

<br/>
<br/>

## 3. React Event Object

이벤트 핸들러는 함수를 동작한 React 이벤트에 액세스할 수 있습니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Football() {
  const shoot = (a, b) => {
    alert(b.type);
  };

  return (
    <button onClick={(event) => shoot("Goal!", event)}>Take the shot!</button>
  );
}

ReactDOM.render(<Football />, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [10 Conditionals](./10%20Conditionals.md) :arrow_forward:
