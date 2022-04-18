# 07 useCallback

useCallback 훅은 props가 변경되지 않는 한 컴포넌트가 다시 렌더링되는 것을 방지합니다.  
useMemo는 메모화된 값을 반환하고 useCallback은 메모화된 함수를 반환한다는 것입니다.

- index.js

```javascript
import { useState, useCallback } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = useCallback(() => {
    setTodos((t) => [...t, "New Todo"]);
  }, [todos]);

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
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

const Todos = ({ todos, addTodo }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
      <button onClick={addTodo}>Add Todo</button>
    </>
  );
};

export default memo(Todos);
```

<br/>
<br/>

:arrow_forward: [08 useMemo](./08%20useMemo.md) :arrow_forward:
