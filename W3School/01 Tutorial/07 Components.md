# 07 Components

## 1. Create Your First Component

React 컴포넌트를 생성할 때, 컴포넌트의 이름은 반드시 대문자로 시작해야합니다.

```javascript
function Car() {
  return <h2>Hi, I am a Car!</h2>;
}
```

<br/>
<br/>

## 2. Rendering a Component

React 애플리케이션에서의 컴포넌트 사용은 일반 HTML과 유사한 문법을 사용합니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Car() {
  return <h2>Hi, I am a Car!</h2>;
}

ReactDOM.render(<Car />, document.getElementById("root"));
```

<br/>
<br/>

## 3. Props

컴포넌트는 props를 사용하여 속성을 전달할 수 있습니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Car(props) {
  return <h2>I am a {props.color} Car!</h2>;
}

ReactDOM.render(<Car color="red" />, document.getElementById("root"));
```

<br/>
<br/>

## 4. Components in Components

컴포넌트 내에 다른 컴포넌트를 사용할 수 있습니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Car() {
  return <h2>I am a Car!</h2>;
}

function Garage() {
  return (
    <>
      <h1>Who lives in my Garage?</h1>
      <Car />
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById("root"));
```

<br/>
<br/>

## 5. Components in Files

React는 코드 재사용성을 위해 컴포넌트를 별도의 파일로 분할하는 것이 좋습니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";
import Car from "./Car.js";

ReactDOM.render(<Car />, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [08 Props](./08%20Props.md) :arrow_forward:
