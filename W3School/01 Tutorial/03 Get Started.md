# 03 Get Started

React를 사용하기 위해서, Node.js에 포함된 npm이 필요합니다.

<br/>

## 1. Setting up a React Environment

npx 와 Node.js가 설치되어 있다면, create-react-app을 사용하여 React에 애플리케이션을 생성할 수 있습니다.

```bash
$ npm uninstall -g create-react-app
$ npx create-react-app my-react-app
```

<br/>
<br/>

## 2. Run the React Application

다음 명령어를 실행하여 React 애플리케이션을 실행합니다.

```bash
$ cd my-react-app
$ npm start
```

<br/>
<br/>

## 3. Modify the React Application

src 폴더 안에 App.js 파일을 열어 HTML 내용을 변경하고 파일을 저장합니다.

```javascript
import React from "react";

function App() {
  return (
    <div className="App">
      <h1>Hello World!</h1>
    </div>
  );
}

export default App;
```

<br/>
<br/>

:arrow_forward: [04 ES6](./04%20ES6.md) :arrow_forward:
