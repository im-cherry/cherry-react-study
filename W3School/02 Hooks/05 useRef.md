# 05 useRef

## 1. Does Not Cause Re-renders

useState 훅을 사용하여 애플리케이션이 렌더링하는 count를 계산하려고 하면,  
이 훅 자체가 다시 렌더링을 일으키기 때문에 무한 루프에 빠지게 됩니다.  
이를 피하기 위해 useRef 훅을 사용할 수 있습니다.

```javascript
import { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom";

function App() {
  const [inputValue, setInputValue] = useState("");
  const count = useRef(0);

  useEffect(() => {
    count.current = count.current + 1;
  });

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h1>Render Count: {count.current}</h1>
    </>
  );
}

ReactDOM.render(<App />, document.getElementById("root"));
```

<br/>
<br/>

## 2. Accessing DOM Elements

React에서 ref 속성을 요소에 추가하여 DOM을 직접 액세스할 수 있습니다.

```javascript
import { useRef } from "react";
import ReactDOM from "react-dom";

function App() {
  const inputElement = useRef();

  const focusInput = () => {
    inputElement.current.focus();
  };

  return (
    <>
      <input type="text" ref={inputElement} />
      <button onClick={focusInput}>Focus Input</button>
    </>
  );
}

ReactDOM.render(<App />, document.getElementById("root"));
```

<br/>
<br/>

## 3. Tracking State Changes

useRef 훅은 이전 상태 값을 추적하는데 사용할 수 있습니다.

```javascript
import { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom";

function App() {
  const [inputValue, setInputValue] = useState("");
  const previousInputValue = useRef("");

  useEffect(() => {
    previousInputValue.current = inputValue;
  }, [inputValue]);

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h2>Current Value: {inputValue}</h2>
      <h2>Previous Value: {previousInputValue.current}</h2>
    </>
  );
}

ReactDOM.render(<App />, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [06 useReducer](./06%20useReducer.md) :arrow_forward:
