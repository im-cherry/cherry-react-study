# 14 Memo

Memo를 사용하면 props가 변경되지 않는 경우, React에서 컴포넌트 렌더링을 스킵합니다.  
이렇게 하면 성능이 향상됩니다.

## 1. Problem

아래의 예에서 Todos 컴포넌트는 할일(todos)이 변경되지 않은 경우에도 다시 렌더링 됩니다.

- index.js

```javascript
import { useState } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState(["todo 1", "todo 2"]);

  const increment = () => {
    setCount((c) => c + 1);
  };

  return (
    <>
      <Todos todos={todos} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById("root"));
```

- Todos.js

```javascript
const Todos = ({ todos }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
    </>
  );
};

export default Todos;
```

<br/>
<br/>

## 2. Solution

위의 문제를 해결하기 위해 Memo를 사용할 수 있습니다.  
Memo를 사용하면 Todos 컴포넌트가 불필요하게 다시 렌더링되지 않습니다.

- index.js

```javascript
import { useState } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState(["todo 1", "todo 2"]);

  const increment = () => {
    setCount((c) => c + 1);
  };

  return (
    <>
      <Todos todos={todos} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById("root"));
```

- Todos.js

```javascript
import { memo } from "react";

const Todos = ({ todos }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
    </>
  );
};

export default memo(Todos);
```

<br/>
<br/>
