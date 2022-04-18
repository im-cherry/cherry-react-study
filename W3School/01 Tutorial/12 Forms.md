# 12 Forms

## 1. Adding Forms in React

HTML과 같이 React는 사용자가 웹 페이지와 상호 작용할 수 있도록 Form을 사용합니다.

```javascript
import { useState } from "react";
import ReactDOM from "react-dom";

function MyForm() {
  const [name, setName] = useState("");

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`The name you entered was: ${name}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Enter your name:
        <input
          type="text"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
      </label>
      <input type="submit" />
    </form>
  );
}

ReactDOM.render(<MyForm />, document.getElementById("root"));
```

<br/>
<br/>

## 2. Multiple Input Fields

각 요소에 name 속성을 추가하여 입력 필드값을 제어할 수 있습니다.

```javascript
import { useState } from "react";
import ReactDOM from "react-dom";

function MyForm() {
  const [inputs, setInputs] = useState({});

  const handleChange = (event) => {
    const name = event.target.name;
    const value = event.target.value;
    setInputs((values) => ({ ...values, [name]: value }));
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log(inputs);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Enter your name:
        <input
          type="text"
          name="username"
          value={inputs.username || ""}
          onChange={handleChange}
        />
      </label>
      <label>
        Enter your age:
        <input
          type="number"
          name="age"
          value={inputs.age || ""}
          onChange={handleChange}
        />
      </label>
      <input type="submit" />
    </form>
  );
}

ReactDOM.render(<MyForm />, document.getElementById("root"));
```

<br/>
<br/>

## 3. Textarea

```javascript
import { useState } from "react";
import ReactDOM from "react-dom";

function MyForm() {
  const [textarea, setTextarea] = useState(
    "The content of a textarea goes in the value attribute"
  );

  const handleChange = (event) => {
    setTextarea(event.target.value);
  };

  return (
    <form>
      <textarea value={textarea} onChange={handleChange} />
    </form>
  );
}

ReactDOM.render(<MyForm />, document.getElementById("root"));
```

<br/>
<br/>

## 4. Select

```javascript
import { useState } from "react";
import ReactDOM from "react-dom";

function MyForm() {
  const [myCar, setMyCar] = useState("Volvo");

  const handleChange = (event) => {
    setMyCar(event.target.value);
  };

  return (
    <form>
      <select value={myCar} onChange={handleChange}>
        <option value="Ford">Ford</option>
        <option value="Volvo">Volvo</option>
        <option value="Fiat">Fiat</option>
      </select>
    </form>
  );
}

ReactDOM.render(<MyForm />, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [13 Router](./13%20Rounter.md) :arrow_forward:
