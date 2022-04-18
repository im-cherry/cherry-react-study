# 06 useReducer

useReducer 훅은 useState 와 유사합니다.  
복잡고 많은 state를 추적하고 있다면 useReducer가 유용할 수 있습니다.  
`useReducer(reducer, initialState)` 훅은 현재 state와 dispatch 메서드를 반환합니다.

```javascript
import { useReducer } from "react";
import ReactDOM from "react-dom";

const initialTodos = [
  {
    id: 1,
    title: "Todo 1",
    complete: false,
  },
  {
    id: 2,
    title: "Todo 2",
    complete: false,
  },
];

const reducer = (state, action) => {
  switch (action.type) {
    case "COMPLETE":
      return state.map((todo) => {
        if (todo.id === action.id) {
          return { ...todo, complete: !todo.complete };
        } else {
          return todo;
        }
      });
    default:
      return state;
  }
};

function Todos() {
  const [todos, dispatch] = useReducer(reducer, initialTodos);

  const handleComplete = (todo) => {
    dispatch({ type: "COMPLETE", id: todo.id });
  };

  return (
    <>
      {todos.map((todo) => (
        <div key={todo.id}>
          <label>
            <input
              type="checkbox"
              checked={todo.complete}
              onChange={() => handleComplete(todo)}
            />
            {todo.title}
          </label>
        </div>
      ))}
    </>
  );
}

ReactDOM.render(<Todos />, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [07 useCallback](./07%20useCallback.md) :arrow_forward:
