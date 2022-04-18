# 10 Conditionals

React에서는 조건부로 컴포넌트를 렌더링할수 있습니다.

<br/>

## 1. Logical && Operator

React 컴포넌트는 && 연산자를 사용하여 조건부 렌더링을 할 수 있습니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function Garage(props) {
  const cars = props.cars;
  return (
    <>
      <h1>Garage</h1>
      {cars.length > 0 && <h2>You have {cars.length} cars in your garage.</h2>}
    </>
  );
}

const cars = ["Ford", "BMW", "Audi"];
ReactDOM.render(<Garage cars={cars} />, document.getElementById("root"));
```

<br/>
<br/>

## 2. Ternary Operator

삼항 연산자를 사용하여 컴포넌트를 조건부로 렌더링 할 수 있습니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

function MissedGoal() {
  return <h1>MISSED!</h1>;
}

function MadeGoal() {
  return <h1>GOAL!</h1>;
}

function Goal(props) {
  const isGoal = props.isGoal;
  return <>{isGoal ? <MadeGoal /> : <MissedGoal />}</>;
}

ReactDOM.render(<Goal isGoal={false} />, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [11 Lists](./11%20Lists.md) :arrow_forward:
