# 09 10 useRef 로 컴포넌트 안의 변수 만들기

## 1. useRef 로 컴포넌트 안의 변수 만들기

useRef Hook 은 DOM 을 선택하는 용도 외에도, 컴포넌트 안에서 조회 및 수정 할 수 있는 변수를 관리하는 용도로 사용할 수 있습니다.

- App.js

  ```javascript
  import React, { userRef } from "react";
  import UserList from "./UserList";

  function App() {
    const users = [
      {
        id: 1,
        username: "velopert",
        email: "public.velopert@gmail.com",
      },
      {
        id: 2,
        username: "tester",
        email: "tester@example.com",
      },
      {
        id: 3,
        username: "liz",
        email: "liz@example.com",
      },
    ];

    const nextId = useRef(4);
    const onCreate = () => {
      nextId.current += 1;
    };

    return <UserList users={users} />;
  }

  export default App;
  ```

- UserList.js

  ```javascript
  import React from "react";

  function User({ user }) {
    return (
      <div>
        <b>{user.username}</b> <span>({user.email})</span>
      </div>
    );
  }

  function UserList({ users }) {
    return (
      <div>
        {users.map((user) => (
          <User user={user} key={user.id} />
        ))}
      </div>
    );
  }

  export default UserList;
  ```

<br/>
<br/>

## 2. 배열에 항목 추가하기

- UserList.js

  ```javascript
  import React from "react";

  function User({ user }) {
    return (
      <div>
        <b>{user.username}</b> <span>({user.email})</span>
      </div>
    );
  }

  function UserList({ users }) {
    return (
      <div>
        {users.map((user) => (
          <User user={user} key={user.id} />
        ))}
      </div>
    );
  }

  export default UserList;
  ```

- CreateUser.js

  ```javascript
  import React from "react";

  function CreateUser({ username, email, onChange, onCreate }) {
    return (
      <div>
        <input
          name="username"
          placeholder="계정명"
          onChange={onChange}
          value={username}
        />
        <input
          name="email"
          placeholder="이메일"
          onChange={onChange}
          value={email}
        />
        <button onClick={onCreate}>등록</button>
      </div>
    );
  }

  export default CreateUser;
  ```

- App.js

  ```javascript
  import React, { useState, useRef } from "react";
  import UserList from "./UserList";
  import CreateUser from "./CreateUser";

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
      },
      {
        id: 2,
        username: "tester",
        email: "tester@example.com",
      },
      {
        id: 3,
        username: "liz",
        email: "liz@example.com",
      },
    ]);

    const nextId = useRef(4);
    const onCreate = () => {
      const user = {
        id: nextId.current,
        username,
        email,
      };
      // setUsers([...users, user]);
      setUsers(users.concat(user));

      setInputs({
        username: "",
        email: "",
      });
      nextId.current += 1;
    };

    return (
      <>
        <CreateUser
          username={username}
          email={email}
          onChange={onChange}
          onCreate={onCreate}
        />
        <UserList users={users} />
      </>
    );
  }

  export default App;
  ```

<br/>
<br/>

## 3. 배열에 항목 제거하기

- UserList.js

  ```javascript
  import React from "react";

  function User({ user, onRemove }) {
    return (
      <div>
        <b>{user.username}</b> <span>({user.email})</span>
        <button onClick={() => onRemove(user.id)}>삭제</button>
      </div>
    );
  }

  function UserList({ users, onRemove }) {
    return (
      <div>
        {users.map((user) => (
          <User user={user} key={user.id} onRemove={onRemove} />
        ))}
      </div>
    );
  }

  export default UserList;
  ```

- App.js

  ```javascript
  import React, { useState, useRef } from "react";
  import UserList from "./UserList";
  import CreateUser from "./CreateUser";

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
      },
      {
        id: 2,
        username: "tester",
        email: "tester@example.com",
      },
      {
        id: 3,
        username: "liz",
        email: "liz@example.com",
      },
    ]);

    const nextId = useRef(4);
    const onCreate = () => {
      const user = {
        id: nextId.current,
        username,
        email,
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

    return (
      <>
        <CreateUser
          username={username}
          email={email}
          onChange={onChange}
          onCreate={onCreate}
        />
        <UserList users={users} onRemove={onRemove} />
      </>
    );
  }

  export default App;
  ```

<br/>
<br/>

## 4. 배열에 항목 수정하기

- App.js

  ```javascript
  import React, { useState, useRef } from "react";
  import UserList from "./UserList";
  import CreateUser from "./CreateUser";

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
        active: false;
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

    return (
      <>
        <CreateUser
          username={username}
          email={email}
          onChange={onChange}
          onCreate={onCreate}
        />
        <UserList users={users} onRemove={onRemove} onToggle={onToggle} />
      </>
    );
  }

  export default App;
  ```

- UserList.js

  ```javascript
  import React from "react";

  function User({ user, onRemove, onToggle }) {
    return (
      <div>
        <b
          style={{ cursor: "pointer", color: user.active ? "green" : "black" }}
          onClick={() => onToggle(user.id)}
        >
          {user.username}
        </b>{" "}
        <span>({user.email})</span>
        <button onClick={() => onRemove(user.id)}>삭제</button>
      </div>
    );
  }

  function UserList({ users, onRemove, onToggle }) {
    return (
      <div>
        {users.map((user) => (
          <User
            user={user}
            key={user.id}
            onRemove={onRemove}
            onToggle={onToggle}
          />
        ))}
      </div>
    );
  }

  export default UserList;
  ```

<br/>
<br/>

:arrow_forward: [11 useEffect를 작업 설정하기](./11%20useEffect%EB%A5%BC%20%EC%9E%91%EC%97%85%20%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0.md) :arrow_forward:
