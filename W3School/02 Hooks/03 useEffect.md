# 03 useEffect

useEffect는 모든 렌더링에서 실행됩니다.
useEffect는 함수, 종속성 두 개의 인자를 가집니다.

<br/>

## 1. No dependency

모든 렌더링과정에서 실행됩니다.

```javascript
useEffect(() => {});
```

<br/>
<br/>

## 2. An empty array

첫 렌더링에서만 실행됩니다.

```javascript
useEffect(() => {}, []);
```

<br/>
<br/>

## 3. Props or state values

첫 렌더링, value 변화 과정에서만 실행됩니다.

```javascript
useEffect(() => {}, [prop, state]);
```

<br/>
<br/>

## 4. Effect Cleanup

useEffect 훅의 끝에 return 함수를 사용하면 clean-up 함수가 실행됩니다.  
언마운트 이전, 업데이트 직전에 어떠한 작업을 수행하고 싶다면 clean-up 함수를 return 합니다.
clean-up 함수는 이전의 값을 바라보고 있습니다.

```javascript
import React, { useState, useEffect } from "react";

export default function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("useEffect !");
    return () => {
      console.log(count);
    };
  }, [count]);

  return (
    <div className="App">
      <h2>{count}</h2>
      <button onClick={() => setCount(count + 1)}>+</button>
    </div>
  );
}
```

<br/>
<br/>

:arrow_forward: [04 useContext](./04%20useContext.md) :arrow_forward:
