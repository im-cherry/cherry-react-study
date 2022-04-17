# 11 useEffect를 작업 설정하기

useEffect 라는 Hook 을 사용하면 컴포넌트가 마운트 됐을 때 (처음 나타났을 때), 언마운트 됐을 때 (사라질 때), 그리고 업데이트 될 때 (특정 props가 바뀔 때) 특정 작업을 처리할 수 있습니다.

- UserList.js

  ```javascript
  import React, { useEffect } from "react";

  function User({ user, onRemove, onToggle }) {
    // 컴포넌트가 처음 나타날때에만 함수 호출
    useEffect(() => {
      console.log("컴포넌트가 화면에 나타남");
      return () => {
        console.log("컴포넌트가 화면에 사라짐");
      };
    }, []);

    // user값이 바뀔때에만 함수 호출
    useEffect(() => {
      console.log("user 값이 설정됨");
      return () => {
        console.log("user 가 바뀌기 전..");
      };
    }, [user]);

    // 컴포넌트가 리렌더링 될 때마다 호출
    useEffect(() => {
      console.log(user);
    });

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

:arrow_forward: [12 useMemo 를 사용하여 연산한 값 재사용하기](./12%20useMemo%20%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC%20%EC%97%B0%EC%82%B0%ED%95%9C%20%EA%B0%92%20%EC%9E%AC%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0.md :arrow_forward:
