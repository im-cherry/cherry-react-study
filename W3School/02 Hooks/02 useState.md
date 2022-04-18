# 02 useState

useState 훅을 사용하면 함수 컴포넌트의 state를 추적할 수 있습니다.

## 1. State

```javascript
import { useState } from "react";
import ReactDOM from "react-dom";

function FavoriteColor() {
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button type="button" onClick={() => setColor("blue")}>
        Blue
      </button>
    </>
  );
}

ReactDOM.render(<FavoriteColor />, document.getElementById("root"));
```

<br/>
<br/>

## 2. Objects and Arrays in State

```javascript
import { useState } from "react";
import ReactDOM from "react-dom";

function Car() {
  const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red",
  });

  const updateColor = () => {
    setCar((previousState) => {
      return { ...previousState, color: "blue" };
    });
  };

  return (
    <>
      <h1>My {car.brand}</h1>
      <p>
        It is a {car.color} {car.model} from {car.year}.
      </p>
      <button type="button" onClick={updateColor}>
        Blue
      </button>
    </>
  );
}

ReactDOM.render(<Car />, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [03 useEffect](./03%20useEffect.md) :arrow_forward:
