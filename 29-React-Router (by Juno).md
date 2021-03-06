# 29-React-Router

## π€·ββοΈ Routing(λΌμ°ν) μ΄λ?

<br/>

> λΌμ°νμ νλ‘μΈμ€μΈλ° μ°λ¦¬κ° λ€νΈμν¬μμ μλ trafficeμ pathλ₯Ό μ ννλ νλ‘μΈμ€μ΄λ€.  
> μ¦, λ€νΈμν¬μμ urlλ₯Ό μ΄μ©νμλ μ΄λ€ λ°μ΄ν°λ₯Ό λ°μμ¬μ§ κ²°μ ν΄μ£Όλκ²
>
> > ννμ΄μ§μ λ€μ΄μμλ -> www.baegofda.com/  
> > νμκ°μμ λλ μλ -> www.baegofda.com/<strong>register</string>  
> > λ‘κ·ΈμΈ νμ΄μ§λ‘ λ€μ΄κ°μλ -> www.baegofda.com/<strong>login</string>  
> > νλ‘ν νμ΄μ§λ‘ λ€μ΄κ°μλ -> www.baegofda.com/<strong>profile</string>
>
> μ κ°μ΄ μ΄λ€ νμ΄μ§λ₯Ό λ³΄μ¬μ€κ²μΈμ§ κ²°μ νκ³  λμμ£Όλκ²  
> `React-Router` λ§κ³ λ `Reach-Router`, `Next.js`λ±μ λμμ΄ μμ΅λλ€.

<br/>

## π Why ?

<br/>

&nbsp;`React` λΏλ§μλ `Vue`, `Angular`, `Svelte`λ±μ **SPA**(Single Page Application)λ₯Ό κ΅¬ννκΈ° μν¨μλλ€.  
SSR λ°©μμ HTML νμ΄μ§κ° λ°λλκ±°μ λ¬λ¦¬ νλμ HTML μμ CSR λ°©μμΌλ‘ λ¦¬λ‘λ λμ§μκ³  λμ μΌλ‘ κ°μ Έμμ λ³΄μ¬μ€λλ€.  
λλ¬Έμ λΆλ§ν¬, νμ΄μ§ λ€λ‘κ°κΈ° μμΌλ‘κ°κΈ°κ° λΆκ°λ₯ν©λλ€. μμκ°μ λ¬Έμ λ₯Ό ν΄κ²°νκΈ°μν΄ Routing μ΄λΌλ κ°λμ΄ μ€μν©λλ€.

[(κ΄λ ¨ μ°Έκ³ ) SSRμ΄λ? - NaverD2](https://d2.naver.com/helloworld/7804182)

[(κ΄λ ¨ μ°Έκ³ ) SPA κ·Έλ¦¬κ³  SSR, CSR](https://velog.io/@ru_bryunak/SPA-%EC%82%AC%EC%9A%A9%EC%97%90%EC%84%9C%EC%9D%98-SSR%EA%B3%BC-CSR)

<br/>

## π μ½λλ‘ μμλ³΄κΈ°

<br/>

> **π Key Point**  
> React-Routerμλ λ€μν μ»΄ν¬λνΈλ€μ΄ μμ΅λλ€.  
> κ·Έ μ€ μ ν¬λ `BrowserRouter`, `Switch`, `Route`, `Link`, `NavLink` λν΄ μμλ³Ό κ² μλλ€.  
> μμ μ»΄ν¬λνΈλ€μ μμΉμ μ¬μ©μ μ€μ μ μΌλ‘ λ΄μ£ΌμκΈΈ λ°λλλ€.

<br/>

&nbsp;μ μ²΄μ νμΌ κ΅¬μ‘°λ μλμ κ°μ΅λλ€.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fz8d4u%2Fbtq2lrBB1W8%2F2xnQBVaLpbjmO4bRcsX4E1%2Fimg.png"/></p>

<br/>

### πΎ μννκΈ°

---

<br/>

&nbsp;λ¨Όμ  react-router-domλ₯Ό μ€μΉν©λλ€.

<br/>

```bash
# npm
npm install react-router-dom
# yarn
yarn add react-router-dom
```

<br/>

### π src>index.js

---

<br/>

&nbsp;λ¨Όμ  index.jsμ μ½λλ μλμ κ°μ΅λλ€.

<br/>

```js
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";
import { BrowserRouter as Router } from "react-router-dom";

ReactDOM.render(
  <Router>
    <App />
  </Router>,
  document.getElementById("root")
);
```

<br/>

&nbsp;Routingμ μν΄ `BrowserRouter` μ»΄ν¬λνΈλ₯Ό μ¬μ©νλ©° νΈμμ aliasλ‘ "Router"λ₯Ό λͺμνμ¬ App.jsμ κ°μΈμ€λλ€.

<br/>

### π src>App.js

---

<br/>

&nbsp;App.jsμ μ½λλ μλμ κ°μ΅λλ€.

<br/>

```js
import { Switch, Route } from "react-router-dom";

const App = () => {
  return (
    <>
      <Header />
      <main className="main">
        <Switch>
          <Route exact path={"/"} component={Home} />
          <Route path={"/Board1"} component={Board1} />
          <Route path={"/Board2"} component={Board2} />
          <Route path={"/Login"} component={Login} />
          <Route path={"/Register"} component={Register} />
        </Switch>
      </main>
    </>
  );
};

export default App;
```

<br/>

&nbsp;λ¨Όμ  `<Route exact path={"/"} component={Home} />` λ΄λΆμ `exact`κ° μλ€λ©΄ λͺ¨λ  pathμ λ΄λΆμ "/"κ° ν¬ν¨λμ΄μκΈ° λλ¬Έμ Routingμ Home μ»΄ν¬λνΈκ° ν¨κ» λ λλ§λ©λλ€.  
 λλ¬Έμ κ΅¬λΆμ λͺνν΄μ£ΌκΈ° μν΄ `exact` μ¬μ©νλ©° `Switch`λ Routing μ ν΄λΉνλ pathκ° μλ€λ©΄ ν΄λΉ ν¨μ€μ μ»΄ν¬λνΈλ₯Ό λ³΄μ¬μ£Όκ³  λλκ² λ©λλ€. λ 404 Pageλ₯Ό μ κ³΅ν  μ μμ΅λλ€.

<br/>

### π src>components>Header.jsx

---

<br/>

&nbsp; μλλ Header μ»΄ν¬λνΈμ μ½λμλλ€.

<br/>

```js
import React from "react";
import "./Header.scss";
import { Link } from "react-router-dom";

const Header = () => {
  return (
    <nav className="nav">
      <h1>React-Router-DOM</h1>
      <ul className="items">
        <li className="item">
          <Link className="link" to="/" exact>
            Home
          </Link>
        </li>
        <li className="item">
          <Link className="link" to="/Board1">
            Board1
          </Link>
        </li>
        <li className="item">
          <Link className="link" to="/Board2">
            Board2
          </Link>
        </li>
      </ul>
    </nav>
  );
};

export default Header;
```

<br/>

&nbsp; Routing μ¦, λ§ν¬λ₯Ό ν΄λ¦­νμ¬ νμ΄μ§λ₯Ό μ΄λνκΈ° μν΄μλ `anchor` νκ·Έλ₯Ό μ¬μ©νμμ΅λλ€. νμ§λ§ `anchor` νκ·Έλ ν΄λ¦­μ λ¦¬λ‘λκ° λκΈ°λλ¬Έμ React-Routerμμλ `Link`νΉμ` NavLink`λ₯Ό μ¬μ©νλ©° μ΄λν  urlμ μ£Όμλ `href`λΌλ attribute μλ `to`λΌλ propsλ₯Ό μ¬μ©νμ¬ λͺμνμ¬μ€λλ€.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fblshbd%2Fbtq2qyfPM8r%2F0VkbR5ed9pIvdgNIhIk4D0%2Fimg.gif"/></p>

<br/>

&nbsp; νμ§λ§ μλΉμ€λ₯Ό μ κ³΅νλ μμ₯μμλ νμ¬μ μλΉμ€κ° μ΄λμ μμΉνκ³ μλμ§ μλ €μ€μΌνλ©° μ΄μ©μλ μ΄λ₯Ό μ κΆλ¦¬κ° μμ΅λλ€.

<br/>

```js
import React from "react";
import "./Header.scss";
import { NavLink } from "react-router-dom";

const Header = () => {
  return (
    <nav className="nav">
      <h1>React-Router-DOM</h1>
      <ul className="items">
        <li className="item">
          <NavLink className="link" to="/" exact>
            Home
          </NavLink>
        </li>
        <li className="item">
          <NavLink className="link" to="/Board1">
            Board1
          </NavLink>
        </li>
        <li className="item">
          <NavLink className="link" to="/Board2">
            Board2
          </NavLink>
        </li>
      </ul>
    </nav>
  );
};

export default Header;
```

<br/>

&nbsp; μ΄μ μλ classλ₯Ό μΆκ°νλ μμΌλ‘ κΈ°λ₯μ μ κ³΅νμμΌλ μμκ°μ΄ `NavLink` μ»΄ν¬λνΈλ₯Ό μ¬μ©νλ©΄ μ½κ² κ΅¬νμ΄ κ°λ₯ν©λλ€.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Feg10Pi%2Fbtq2iWhYm42%2F7MMQCKAeYtB717XrTv8uik%2Fimg.gif"/></p>

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcl23cY%2Fbtq2qxgVrVG%2FXenTGxidHsGkkUI4OLPDQ1%2Fimg.gif"/></p>

<br/>

&nbsp; μμ κ°μ΄ μλμ μΌλ‘ `active` λΌλ classκ° μΆκ°μ μΌλ‘ μκΈ°κΈ°λλ¬Έμ μ½κ² μ¬μ©μ΄ κ°λ₯ν©λλ€.

<br/>

```js
import React from "react";
import "./Header.scss";
import { NavLink } from "react-router-dom";

const Header = () => {
  return (
    <nav className="nav">
      <h1>React-Router-DOM</h1>
      <ul className="items">
        <li className="item">
          <NavLink className="link" to="/" activeClassName="toggle" exact>
            Home
          </NavLink>
        </li>
        <li className="item">
          <NavLink className="link" to="/Board1" activeClassName="toggle">
            Board1
          </NavLink>
        </li>
        <li className="item">
          <NavLink className="link" to="/Board2" activeClassName="toggle">
            Board2
          </NavLink>
        </li>
      </ul>
    </nav>
  );
};

export default Header;
```

<br/>

λ§μ½ μμ κΈ°λ₯μ μ κ³΅ν  μ classNameμ `active` κ°μλ λ€λ₯Έ classNameμΌλ‘ λ³κ²½νκ³  μΆλ€λ©΄ μμκ°μ΄ `activeClassName` μ΄λΌλ propsλ₯Ό μ¬μ©νμ¬ λ³κ²½μ΄ κ°λ₯ν©λλ€.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FyedZZ%2Fbtq2noEGWwD%2FeX9LFMsIZhiUKcHjlKZzK1%2Fimg.gif"/></p>

<br/>

[λ¦¬μ‘νΈ λΌμ°ν° κ³΅μ μ¬μ΄νΈ](https://reactrouter.com/)

[λΌμ°ν°λ΄μ μ»΄ν¬λνΈμ propsλ₯Ό λκΈ°λ €λ©΄?](https://mingcoder.me/2019/12/04/Programming/React/react-router-component-vs-render/)

π
