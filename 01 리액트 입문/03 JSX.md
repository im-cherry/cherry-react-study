# 03 JSX

JSX는 리액트에서 생김새를 정의할 때, 사용하는 문법입니다.  
리액트 컴포넌트 파일에서 XML 형태로 코드를 작성하면 babel이 JSX를 JavaScript로 변환해줍니다.

<br />

## 1. 꼭 닫혀야 하는 태그

- 태그를 열었으면 꼭, `<div></div>` 이렇게 닫아주어야 합니다.

<br/>
<br/>

## 2. 꼭 감싸져야 하는 태그

- 두가지 이상의 태그는 무조건 하나의 태그로 감싸져있어야 합니다.
- 올바른 예시

  ```javascript
  import React from "react";
  import Hello from "./Hello";

  function App() {
    return (
      <>
        <Hello />
        <div>안녕히계세요</div>
      </>
    );
  }

  export default App;
  ```

- 잘못된 예시

  ```javascript
  import React from 'react';
  import Hello from './Hello';

  function App() {
  return (
      <Hello />
      <div>안녕히계세요.</div>
  );
  }

  export default App;
  ```

<br/>
<br/>

## 3. JSX 안에 자바스크립트 값 사용하기

- JSX 내부에 자바스크립트 변수를 보여줘야 할 때에는 `{}` 으로 감싸서 보여줍니다.

  ```javascript
  import React from "react";
  import Hello from "./Hello";

  function App() {
    const name = "react";
    return (
      <>
        <Hello />
        <div>{name}</div>
      </>
    );
  }

  export default App;
  ```

<br/>
<br/>

## 4. style과 className

- 인라인 스타일은 객체 형태로 작성을 해야 하며, `background-color` 처럼 `-` 로 구분되어 있는 이름들은 `backgroundColor` 처럼 camelCase 형태로 네이밍 해주어야 합니다.
- CSS class 를 설정 할 때에는 `class=` 가 아닌 `className=` 으로 설정을 해주어야 합니다.

  ```javascript
  import React from "react";
  import "./App.css";

  function App() {
    const style = {
      backgroundColor: "black",
      color: "aqua",
      fontSize: 24, // 기본 단위 px
    };

    return (
      <>
        <div style={style}>리액트</div>
        <div className="gray-box"></div>
      </>
    );
  }

  export default App;
  ```

<br/>
<br/>

## 5. 주석

- JSX 내부의 주석은 `{/* 이런 형태로 */}` 작성합니다.
- 열리는 태그 내부에서는 `// 이런 형태로` 도 주석 작성이 가능합니다.

  ```javascript
  import React from "react";
  import Hello from "./Hello";
  import "./App.css";

  function App() {
    return (
      <>
        {/* 주석은 화면에 보이지 않습니다 */}
        <Hello
        // 열리는 태그 내부에서는 이렇게 주석을 작성 할 수 있습니다.
        />
      </>
    );
  }

  export default App;
  ```

<br/>
<br/>

:arrow_forward: [04 props를 통해 컴포넌트에게 값 전달하기](./04%20props%EB%A5%BC%20%ED%86%B5%ED%95%B4%20%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%97%90%EA%B2%8C%20%EA%B0%92%20%EC%A0%84%EB%8B%AC%ED%95%98%EA%B8%B0.md) :arrow_forward:
