# 04 useContext

React Context는 상태를 전역적으로 관리하는 방법입니다.

- `createContext` 를 import하여 초기화합니다.
- 컨텍스트 Provider 를 사용하여 상태 컨텍스트가 필요한 컴포넌트를 wrapping 합니다.
- 컨텍스트 Provider 에서 자식 컴포넌트에 상태 값을 제공합니다.
- 자식 컴포넌트에서 컨텍스트를 사용하려면 `useContext`를 사용하여 액세스합니다.

```javascript
import { useState, createContext, useContext } from "react";
import ReactDOM from "react-dom";

const UserContext = createContext(); // 초기화

function Component1() {
  const [user, setUser] = useState("Jesse Hall");

  return (
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </UserContext.Provider>
  );
}

function Component2() {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 />
    </>
  );
}

function Component3() {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 />
    </>
  );
}

function Component4() {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 />
    </>
  );
}

function Component5() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

ReactDOM.render(<Component1 />, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [05 useRef](./05%20useRef.md) :arrow_forward:
