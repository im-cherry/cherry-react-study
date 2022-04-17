# 04 props를 통해 컴포넌트에게 값 전달하기

어떠한 값을 컴포넌트에게 전달해줘야 할 때, props 를 사용합니다.

<br />

## 1. props의 기본 사용법

App 컴포넌트에서 Hello 컴포넌트를 사용 할 때 name 이라는 값을 전달해주고 싶을 때

- App.js

  ```javascript
  import React from "react";
  import Hello from "./Hello";

  function App() {
    return <Hello name="react" />;
  }

  export default App;
  ```

- Hello.js

  ```javascript
  import React from "react";

  function Hello(props) {
    return <div>안녕하세요 {props.name}</div>;
  }

  export default Hello;
  ```

<br/>
<br/>

## 2. 여러 개의 props, 비구조화 할당, defaultProps로 기본값 설정

- App.js

  ```javascript
  import React from "react";
  import Hello from "./Hello";

  function App() {
    return (
      <>
        <Hello name="react" color="red" />
        <Hello color="pink" />
      </>
    );
  }

  export default App;
  ```

- Hello.js

  ```javascript
  import React from "react";

  function Hello({ color, name = "이름없음" }) {
    return <div style={{ color }}>안녕하세요 {name}</div>;
  }

  export default Hello;
  ```

<br/>
<br/>

## 3. props.children

컴포넌트 태그 사이에 넣은 값을 조회하고 싶을 땐, `props.children` 을 조회하면 됩니다.

- App.js

  ```javascript
  import React from "react";
  import Hello from "./Hello";
  import Wrapper from "./Wrapper";

  function App() {
    return (
      <Wrapper>
        <Hello name="react" color="red" />
        <Hello color="pink" />
      </Wrapper>
    );
  }

  export default App;
  ```

- Hello.js

  ```javascript
  import React from "react";

  function Hello({ color, name = "이름없음" }) {
    return <div style={{ color }}>안녕하세요 {name}</div>;
  }

  export default Hello;
  ```

- Wrapper.js

  ```javascript
  import React from "react";

  function Wrapper({ children }) {
    const style = {
      border: "2px solid black",
      padding: "16px",
    };
    return <div style={style}>{children}</div>;
  }

  export default Wrapper;
  ```

<br/>
<br/>

:arrow_forward: [05 조건부 렌더링](./05%20%EC%A1%B0%EA%B1%B4%EB%B6%80%20%EB%A0%8C%EB%8D%94%EB%A7%81.md) :arrow_forward:
