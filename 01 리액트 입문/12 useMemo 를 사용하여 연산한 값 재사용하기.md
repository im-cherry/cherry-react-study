# 12 useMemo 를 사용하여 연산한 값 재사용하기

성능 최적화를 위하여 연산된 값을 useMemo라는 Hook 을 사용하여 재사용할 수 있습니다.

- App.js

```javascript
import React, { useState, useRef, useMemo } from "react";
import UserList from "./UserList";
import CreateUser from "./CreateUser";

function countActiveUsers(users) {
  console.log("활성 사용자 수를 세는중...");
  return users.filter((user) => user.active).length;
}

function App() {
  const [inputs, setInputs] = useState({
    username: "",
    email: "",
  });
  const { username, email } = inputs;

  const onChange = (e) => {
    const { name, value } = e.target;
    setInputs({
      ...inputs,
      [name]: value,
    });
  };

  const [users, setUsers] = useState([
    {
      id: 1,
      username: "velopert",
      email: "public.velopert@gmail.com",
      active: true,
    },
    {
      id: 2,
      username: "tester",
      email: "tester@example.com",
      active: false,
    },
    {
      id: 3,
      username: "liz",
      email: "liz@example.com",
      active: false,
    },
  ]);

  const nextId = useRef(4);
  const onCreate = () => {
    const user = {
      id: nextId.current,
      username,
      email,
      active: false,
    };
    // setUsers([...users, user]);
    setUsers(users.concat(user));

    setInputs({
      username: "",
      email: "",
    });
    nextId.current += 1;
  };
  const onRemove = (id) => {
    setUsers(users.filter((user) => user.id !== id));
  };
  const onToggle = (id) => {
    setUsers(
      users.map((user) =>
        user.id === id ? { ...user, active: !user.active } : user
      )
    );
  };

  const count = useMemo(() => countActiveUsers(users), [users]);
  return (
    <>
      <CreateUser
        username={username}
        email={email}
        onChange={onChange}
        onCreate={onCreate}
      />
      <UserList users={users} onRemove={onRemove} onToggle={onToggle} />
      <div>활성사용자 수 : {count}</div>
    </>
  );
}

export default App;
```

<br/>
<br/>

:arrow_forward: [13 useCallback 을 사용하여 함수 재사용하기](./13%20useCallback%20%EC%9D%84%20%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC%20%ED%95%A8%EC%88%98%20%EC%9E%AC%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0.md):arrow_forward:
