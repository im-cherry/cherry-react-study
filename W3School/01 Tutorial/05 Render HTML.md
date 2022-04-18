# 05 Render HTML

React는 `ReactDOM.render()`라는 함수를 사용하여 HTML을 웹 페이지에 렌더링합니다.

<br/>

## 1. The Render Function

`ReactDOM.render()` 함수는 HTML 코드와 HTML 요소라는 두 개의 인수를 사용합니다.  
지정된 HTML 요소 내부에 지정된 HTML 코드를 표시합니다.  
root 는 public 디렉토리 안에 index.html 파일에 렌더링됩니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

ReactDOM.render(<p>Hello</p>, document.getElementById("root"));
```

<br/>
<br/>

## 2. The HTML Code

HTML 코드는 JavaScript 코드 내부에 HTML 태그를 작성할 수 있는 JSX를 사용합니다.

```javascript
import React from "react";
import ReactDOM from "react-dom";

const myElement = (
  <table>
    <tr>
      <th>Name</th>
    </tr>
    <tr>
      <td>John</td>
    </tr>
    <tr>
      <td>Elsa</td>
    </tr>
  </table>
);

ReactDOM.render(myElement, document.getElementById("root"));
```

<br/>
<br/>

:arrow_forward: [06 JSX](./06%20JSX.md) :arrow_forward:
