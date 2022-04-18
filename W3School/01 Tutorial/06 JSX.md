# 06 JSX

## 1. What is JSX?

JSX는 JavaScript XML의 약자입니다.  
JSX를 사용하면 React에서 HTML을 작성할 수 있습니다.

<br/>
<br/>

## 2. Coding JSX?

```javascript
import React from "react";
import ReactDOM from "react-dom";

const myElement = <h1>I Love JSX!</h1>;

ReactDOM.render(myElement, document.getElementById("root"));
```

<br/>
<br/>

## 3. Expressions in JSX

JSX를 사용하면 중괄호 `{}`안에 표현식을 작성할 수 있습니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

const myElement = <h1>React is {5 + 5} times better with JSX</h1>;

ReactDOM.render(myElement, document.getElementById("root"));
```

<br/>
<br/>

## 4. Inserting a Large Block of HTML

여러 줄에 HTML을 작성하려면 HTML을 괄호 안에 넣으세요.

```javascript
import React from "react";
import ReactDOM from "react-dom";

const myElement = (
  <ul>
    <li>Apples</li>
    <li>Bananas</li>
    <li>Cherries</li>
  </ul>
);

ReactDOM.render(myElement, document.getElementById("root"));
```

<br/>
<br/>

## 5. One Top Level Element

HTML 코드는 하나의 최상위 요소로 wrapping 되어야 합니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

const myElement = (
  <div>
    <h1>I am a Header.</h1>
    <h1>I am a Header too.</h1>
  </div>
);

ReactDOM.render(myElement, document.getElementById("root"));
```

<br/>
<br/>

## 6. Elements Must be Closed

JSX는 XML 규칙을 따르므로 HTML 요소를 제대로 닫아야 합니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

const myElement = <input type="text" />;

ReactDOM.render(myElement, document.getElementById("root"));
```

<br/>
<br/>

## 7. Attribute class = className

JSX는 class 키워드를 className 으로 사용합니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";
import "./mystyle.css";

const myElement = <h1 className="myclass">Hello World</h1>;

ReactDOM.render(myElement, document.getElementById("root"));
```

<br/>
<br/>

## 8. Conditions

JSX에서 조건문을 사용할 때, 삼항 표현식을 사용하면 좋습니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

const x = 5;

const myElement = <h1>{x < 10 ? "Hello" : "Goodbye"}</h1>;

ReactDOM.render(myElement, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [07 Components](./07%20Components.md) :arrow_forward:
