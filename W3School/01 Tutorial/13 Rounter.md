# 13 Router

## 1. Add React Router

애플리케이션에 React Router 를 추가하려면 터미널에서 다음 명령어를 실행합니다.

```bash
$ npm i -D react-router-dom
$ npm i -D react-router-dom@latest
```

<br/>
<br/>

## 2. Folder Structure

여러 페이지 경로가 있는 애플리케이션을 만들려면 먼저 파일 구조부터 만들어야합니다.

- src/pages/ :
  - Layout.js
  - Home.js
  - Blogs.js
  - Contact.js
  - NoPage.js

<br/>
<br/>

## 3. Basic Usage

index.js 에서 Router를 사용합니다.

```javascript
import ReactDOM from "react-dom";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Layout from "./pages/Layout";
import Home from "./pages/Home";
import Blogs from "./pages/Blogs";
import Contact from "./pages/Contact";
import NoPage from "./pages/NoPage";

export default function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Layout />}>
          <Route index element={<Home />} />
          <Route path="blogs" element={<Blogs />} />
          <Route path="contact" element={<Contact />} />
          <Route path="*" element={<NoPage />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
}

ReactDOM.render(<App />, document.getElementById("root"));
```

<br/>
<br/>

## 4. Example Explained

먼저 컨텐츠를 `<BrowserRouter>`로 wrapping 합니다.  
그 다음 `<Routes>`를 정의합니다. 하나의 애플리케이션은 여러 `<Routes>`를 가질 수 있습니다.  
중첩된 `<Route>`는 상위 경로를 상속하여 경로를 설정합니다.  
경로를 `*`로 설정하면 정의되지 않은 모든 URL에 대한 포괄적인 역할을 합니다.

<br/>
<br/>

## 5. Pages / Components

Layout 컴포넌트는 `<Outlet>` 과 `<Link>` 요소를 가지고 있습니다.  
`<Outlet>`은 현재 선택된 경로를 렌더링 합니다.  
`<Link>`는 URL을 설정하고 인터넷 사용기록을 추적하는데 사용합니다.  
`<Layout>`은 공통 컨텐츠를 삽입하는 공유 컴포넌트 입니다.

- Layout.js

  ```javascript
  import { Outlet, Link } from "react-router-dom";

  const Layout = () => {
    return (
      <>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/blogs">Blogs</Link>
            </li>
            <li>
              <Link to="/contact">Contact</Link>
            </li>
          </ul>
        </nav>

        <Outlet />
      </>
    );
  };

  export default Layout;
  ```

- Home.js

  ```javascript
  const Home = () => {
    return <h1>Home</h1>;
  };

  export default Home;
  ```

- Blogs.js

  ```javascript
  const Blogs = () => {
    return <h1>Blog Articles</h1>;
  };

  export default Blogs;
  ```

- Contact.js

  ```javascript
  const Contact = () => {
    return <h1>Contact Me</h1>;
  };

  export default Contact;
  ```

- NoPage.js

  ```javascript
  const NoPage = () => {
    return <h1>404</h1>;
  };

  export default NoPage;
  ```

<br/>
<br/>

:arrow_forward: [14 Memo](./14%20Memo.md) :arrow_forward:
