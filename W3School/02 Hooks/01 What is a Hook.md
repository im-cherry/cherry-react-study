# 01 What is a Hook?

## 1. What is a Hook?

Hooks는 state 및 lifecycle 메서드와 같은 React 기능에 사용할 수 있습니다.

```javascript
import React, { useState } from "react";
import ReactDOM from "react-dom";

function FavoriteColor() {
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button type="button" onClick={() => setColor("blue")}>
        Blue
      </button>
      <button type="button" onClick={() => setColor("red")}>
        Red
      </button>
      <button type="button" onClick={() => setColor("pink")}>
        Pink
      </button>
      <button type="button" onClick={() => setColor("green")}>
        Green
      </button>
    </>
  );
}

ReactDOM.render(<FavoriteColor />, document.getElementById("root"));
```

<br/>
<br/>

## 2. Hook Rules

Hook에는 3가지 규칙이 있습니다.

- React 함수 컴포넌트 내에서만 호출할 수 있습니다.
- Hooks는 컴포넌트의 최상위 수준에서만 호출할 수 있습니다.
- Hooks는 조건부일 수 없습니다.

<br/>
<br/>

:arrow_forward: [02 useState](./02%20useState.md) :arrow_forward:
