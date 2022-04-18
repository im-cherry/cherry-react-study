# 08 Props

props는 React 컴포넌트에 전달되는 인자입니다.

<br/>

## 1. React Props

React Props는 JavaScript의 함수 인자와 비슷합니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Car(props) {
  return <h2>I am a {props.brand}!</h2>;
}

const myElement = <Car brand="Ford" />;

ReactDOM.render(myElement, document.getElementById("root"));
```

<br/>
<br/>

## 2. Pass Data

Props는 매개변수로서 한 컴포넌트에서 다른 컴포넌트로 데이터를 전달합니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Car(props) {
  return <h2>I am a {props.brand}!</h2>;
}

function Garage() {
  const carName = "Ford";
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <Car brand={carName} />
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [09 Events](./09%20Events.md) :arrow_forward:
