# 07 input 상태 관리하기

리액트에서 사용자가 입력 할 수 있는 input 태그의 상태를 관리하는 방법을 알아보겠습니다.

## 1. input 상태 관리하기

- InputSample.js

  ```javascript
  import React, { useState } from "react";

  function InputSample() {
    const [text, setText] = useState("");

    const onChange = (e) => {
      setText(e.target.value);
    };

    const onReset = () => {
      setText("");
    };

    return (
      <div>
        <input onChange={onChange} value={text} />
        <button onClick={onReset}>초기화</button>
        <div>
          <b>값 : {text}</b>
        </div>
      </div>
    );
  }

  export default InputSample;
  ```

- App.js

  ```javascript
  import React from "react";
  import InputSample from "./InputSample";

  function App() {
    return <InputSample />;
  }

  export default App;
  ```

<br/>
<br/>

## 2. 여러개의 input 상태 관리하기

- InputSample.js

  ```javascript
  import React, { useState } from "react";

  function InputSample() {
    const [inputs, setInputs] = useState({
      name: "",
      nickname: "",
    });
    const { name, nickname } = inputs;

    const onChange = (e) => {
      const { value, name } = e.target;
      setInputs({
        ...inputs,
        [name]: value,
      });
    };
    const onReset = (e) => {
      setInputs({
        name: "",
        nickname: "",
      });
    };

    return (
      <div>
        <input
          name="name"
          placeholder="이름"
          onChange={onChange}
          value={name}
        />
        <input
          name="nickname"
          placeholder="닉네임"
          onChange={onChange}
          value={nickname}
        />
        <button onClick={onReset}>초기화</button>
        <div>
          <b>값: </b>
          {name} ({nickname})
        </div>
      </div>
    );
  }

  export default InputSample;
  ```

- App.js

  ```javascript
  import React from "react";
  import InputSample from "./InputSample";

  function App() {
    return <InputSample />;
  }

  export default App;
  ```

<br/>
<br/>

:arrow_forward: [08 배열 렌더링하기](./08%20%EB%B0%B0%EC%97%B4%20%EB%A0%8C%EB%8D%94%EB%A7%81%ED%95%98%EA%B8%B0.md) :arrow_forward:
