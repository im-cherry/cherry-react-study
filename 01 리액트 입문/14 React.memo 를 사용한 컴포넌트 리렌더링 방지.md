# 14 React.memo 를 사용한 컴포넌트 리렌더링 방지

컴포넌트의 props 가 바뀌지 않았다면, React.memo 라는 함수를 사용하여 리렌더링을 방지하고 컴포넌트의 리렌더링 성능 최적화할 수 있다.

- CreateUser.js

  ```javascript
  import React from 'react';

  ...

  export default React.memo(CreateUser);
  ```

- UserList.js

  ```javascript
  import React from 'react';

  ...

  export default React.memo(UserList);
  ```

- App.js

  ```javascript
  import React, { useRef, useState, useMemo, useCallback } from "react";
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
    const onChange = useCallback((e) => {
      const { name, value } = e.target;
      setInputs((inputs) => ({
        ...inputs,
        [name]: value,
      }));
    }, []);
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
    const onCreate = useCallback(() => {
      const user = {
        id: nextId.current,
        username,
        email,
      };
      setUsers((users) => users.concat(user));

      setInputs({
        username: "",
        email: "",
      });
      nextId.current += 1;
    }, [username, email]);

    const onRemove = useCallback((id) => {
      setUsers((users) => users.filter((user) => user.id !== id));
    }, []);
    const onToggle = useCallback((id) => {
      setUsers((users) =>
        users.map((user) =>
          user.id === id ? { ...user, active: !user.active } : user
        )
      );
    }, []);
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

:arrow_forward: [15 useReducer 를 사용하여 상태 업데이트 로직 분리하기](./15%20useReducer%20%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC%20%EC%83%81%ED%83%9C%20%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8%20%EB%A1%9C%EC%A7%81%20%EB%B6%84%EB%A6%AC%ED%95%98%EA%B8%B0.md):arrow_forward:
