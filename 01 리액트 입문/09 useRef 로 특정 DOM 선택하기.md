# 09 useRef 로 특정 DOM 선택하기

JavaScript 를 사용 할 때에는, 우리가 특정 DOM 을 선택해야 하는 상황에 getElementById, querySelector 같은 DOM Selector 함수를 사용해서 DOM 을 선택합니다. 리액트를 사용하는 프로젝트에서도 가끔씩 DOM 을 직접 선택해야 하는 상황이 발생 할 때도 있습니다. 그럴 땐, 리액트에서 ref 라는 것을 사용합니다.

- InputSample.js

  ```javascript
  import React, { useState, useRef } from "react";

  function InputSample() {
    const [inputs, setInputs] = useState({
      name: "",
      nickname: "",
    });
    const nameInput = useRef();
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
      nameInput.current.focus(); // .current값은 우리가 원하는 DOM을 가리킴
    };

    return (
      <div>
        <input
          name="name"
          placeholder="이름"
          onChange={onChange}
          value={name}
          ref={nameInput}
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

<br/>
<br/>

:arrow_forward: [10 useRef 로 컴포넌트 안의 변수 만들기](./10%20useRef%20%EB%A1%9C%20%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%20%EC%95%88%EC%9D%98%20%EB%B3%80%EC%88%98%20%EB%A7%8C%EB%93%A4%EA%B8%B0.md) :arrow_forward:
