# 06 useState를 통해 컴포넌트에서 바뀌는 값 관리하기

## 1. useState

- Counter.js

  ```javascript
  import React, { useState } from "react";

  function Counter() {
    const [number, setNumber] = useState(0);

    const onIncrease = () => {
      setNumber(number + 1);
    };
    const onDecrease = () => {
      setNumber(number - 1);
    };

    return (
      <div>
        <h1>{number}</h1>
        <button onClick={onIncrease}>+1</button>
        <button onClick={onDecrease}>-1</button>
      </div>
    );
  }

  export default Counter;
  ```

- App.js

  ```javascript
  import React from "react";
  import Counter from "./Counter";

  function App() {
    return <Counter />;
  }

  export default App;
  ```

<br/>
<br/>

## 2. 함수형 업데이트

- Counter.js

  ```javascript
  import React, { useState } from "react";

  function Counter() {
    const [number, setNumber] = useState(0);

    const onIncrease = () => {
      setNumber((prevNumber) => prevNumber + 1);
    };
    const onDecrease = () => {
      setNumber((prevNumber) => prevNumber - 1);
    };

    return (
      <div>
        <h1>{number}</h1>
        <button onClick={onIncrease}>+1</button>
        <button onClick={onDecrease}>-1</button>
      </div>
    );
  }

  export default Counter;
  ```

<br/>
<br/>

:arrow_forward: [07 input 상태 관리하기](./07%20input%20%EC%83%81%ED%83%9C%20%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0.md) :arrow_forward:
