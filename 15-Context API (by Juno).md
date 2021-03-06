# 15-Context API

## ๐ Context API๋?

<br/>

> ๋ฆฌ์กํธ 16.3๋ถํฐ ์ ์ ๋ฆด๋ฆฌ์ฆ๋ ์ปดํฌ๋ํธ์ ๋ ๋ฒจ๊ณผ๋ ์๊ด์์ด props๋ฅผ ์์ ๋กญ๊ฒ ์ฌ์ฉ๊ฐ๋ฅํ๊ฒํ๋ Hooks์ด๋ฉฐ state management์๋๋ค.

<br/>

## 1. ๐ ๋ง๋ณด๊ธฐ

<br/>

&nbsp; ์๋์ ๊ฐ์ ์ปดํฌ๋ํธ ๊ตฌ์กฐ๋ฅผ ๊ฐ์ง ์ฌ์ดํธ๊ฐ ์๋ค๊ณ  ๊ฐ์ ํ์ฌ๋ด์๋ค.

<br/>

<p align="center"><img src="https://i.imgur.com/tmOeRAT.png"/></p>

<br/>

&nbsp; state์ value๊ฐ์ ๋ณด์ฌ์ฃผ๋ ์ปดํฌ๋ํธ๋ F์ J๋ผ๊ณ  ๊ฐ์ ํ๊ณ  ๊ฐ์ ๋ณํ์ํค๋
์ด๋ฒคํธ๋ G ์ปดํฌ๋ํธ์์ ๋ฐ์ํ๋ค๋ ๊ฐ์  ํ  ๊ฒฝ์ฐ value๋ F์ปดํฌ๋ํธ๊น์ง ํด๋น value๋ฅผ ์ฌ์ฉํ์ง๋ ์๋ A,B๋ผ๋ ์ปดํฌ๋ํธ์ props๋ฅผ ๊ฑฐ์ณ์ผํฉ๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FKq24c%2Fbtq1tCegRlf%2FkU8KWl6XOi2XgbycSL2VG0%2Fimg.png"/></p>

<br/>

&nbsp; handleSetValue()๋ํ A, B, E ์ปดํฌ๋ํธ๋์ props๋ฅผ ์ ๋ฌ๋ฐ์์ผ ์ต์ข G์ปดํฌ๋ํธ์ ์ ๋ฌ์ด ๋ฉ๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnTZrJ%2Fbtq1yXVKTbG%2FColU6Mwd1JnL5jzQ2XFwQ0%2Fimg.png"/></p>

<br/>

&nbsp; ์ด๋ฌํ ๋ฌธ์ ์ ์ ํด๊ฒฐ ํด์ฃผ๋ Hooks๊ฐ ๋ฐ๋ก Context API์๋๋ค.

<br/>

<p align="center"><img src="https://i.imgur.com/iyNKCIz.png"/></p>

<br/>

&nbsp; Context API๋ ์ฌ์ค ๋จ์ `props drilling`์ ํด๊ฒฐํ๊ธฐ ์ํ ์๋ฃจ์์ด์์ผ๋ฉฐ ์ง๊ธ์ ๊ธฐ์กด์ state management๋์ฒด์ ๋ก๋ ๋ง์ด ํ์ฉ ๋๊ณ ์์ต๋๋ค.

<br/>

[์ฐธ๊ณ ](https://tsh.io/state-of-frontend/#future-of-frontend)

<br/>

### ๐ ์ฝ๋๋ก ์์๋ณด๊ธฐ

---

<br/>

&nbsp;์ ์ฒด์ ํ์ผ ๊ตฌ์กฐ๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FejGw65%2Fbtq1z3IaguX%2FhVLLgxlU0HYJaFVyR5vDHK%2Fimg.png"/></p>

<br/>

> **๐ Key Point**  
> context API๋ 4๊ฐ์ง์ ์ฉ์ด๊ฐ ๋์ต๋๋ค.
>
> 1. createContext(defalutValue) - context API๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํ ์ ์ธ์๋๋ค.
> 2. Context.Provider - ์ ๊ณต์ ์ฆ, ์ฌ์ฉํ  state๋ฅผ ์ ๊ณตํด์ค๋๋ค.
> 3. Context.Consumer - ์ฌ์ฉ์,์๋น์ ์ฆ, ๋ฐ์ดํฐ๋ฅผ ์ฌ์ฉํ  ์ฃผ์ฒด์๋๋ค. Provider์ ์ํ๋ฅผ ๋ฐ๋ผ๋ณด๊ณ ์์ต๋๋ค.
> 4. useContext(Context) - ์ฌ์ฉํ๊ณ ์ ํ๋ Context์ value์ ์ ๊ทผํฉ๋๋ค.
>
> ์ด๋ฌํ ์ฉ์ด๋ค์ด ๋์ฌ๊ฒ์ด๋ฉฐ ์ค์ ์ผ๋ก ๋ณด์๋ฉด ๋ฉ๋๋ค.

<br/>

### ๐ src>App.js

---

<br/>

&nbsp;ํ์คํธ๋ฅผ ์ํ์ฌ App.js์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import React from "react";
import NumberProvider from "./provider/NumberProvider";
import ThemProvider from "./provider/ThemProvider";
import Page from "./routes/Page";

const App = () => {
  return (
    <ThemProvider>
      <NumberProvider>
        <Page />
      </NumberProvider>
    </ThemProvider>
  );
};
export default App;
```

<br/>

```js
import React from "react";
import Button from "../components/Button";
import Content from "../components/Content";
import Header from "../components/Header";

const Page = () => {
  return (
    <div>
      <Header />
      <Button />
      <Content />
    </div>
  );
};

export default Page;
```

<br/>

&nbsp; ํด๋น ์ปดํฌ๋ํธ๋ Route์ ์ญํ ๋ง ํ๊ณ ์์ผ๋ฉฐ ์ด๋ ํ props๋ ๋ฐ์ง ์๊ณ ์์ต๋๋ค.

<br/>

### ๐ src>context>NumberContext.js

---

<br/>

&nbsp; ๋จผ์  number๊ฐ์ ๋ณ๊ฒฝํ๋ ์์๋ฅผ ์์ ๋ณด๊ฒ ์ต๋๋ค. NumberContext์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import { createContext } from "react";

const NumberContext = createContext({
  number: 0,
  increase: () => {},
  decrease: () => {},
});

export default NumberContext;
```

<br/>

&nbsp; createContext()๋ฅผ ์ฌ์ฉํ์๊ณ  ๊ธฐ๋ณธ value๊ฐ๋ค์ ๊ฐ์ง๊ณ ์์ต๋๋ค.

<br/>

### ๐ src>provider>NumberProvider.js

---

<br/>

&nbsp; NumberProvider์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import React, { useState } from "react";
import NumberContext from "../context/NumberContext";

const NumberProvider = ({ children }) => {
  const increase = () => {
    setNumber((prevState) => {
      return {
        ...prevState,
        number: prevState.number + 1,
      };
    });
  };

  const decrease = () => {
    setNumber((prevState) => {
      return {
        ...prevState,
        number: prevState.number - 1,
      };
    });
  };

  const initialState = {
    number: 0,
    increase,
    decrease,
  };

  const [number, setNumber] = useState(initialState);

  return (
    <NumberContext.Provider value={number}>{children}</NumberContext.Provider>
  );
};

export default NumberProvider;
```

<br/>

&nbsp; createContext()๋ฅผ ์ฌ์ฉํ์๊ธฐ๋๋ฌธ์ NumberContext.Provider๋ฅผ ์ฌ์ฉ ํ  ์ ์๊ฒ ๋์๊ณ  value๋ผ๋ props์ number๋ฅผ ๋ด๊ณ ์์ผ๋ฉฐ number๋ ์์์ ๋ช์ํ number, increase, decrease๋ฅผ ๋ด๊ณ ์์ต๋๋ค.

<br/>

### ๐ src>components>Header.jsx

---

<br/>

&nbsp; Header์ปดํฌ๋ํธ์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import React, { useContext } from "react";
import NumberContext from "../context/NumberContext";
import ThemBtn from "./ThemBtn";

const Header = () => {
  const value = useContext(NumberContext);

  return (
    <>
      <div>{value.number}</div>
      <ThemBtn />
    </>
  );
};

export default Header;
```

<br/>

&nbsp; ํด๋น ์ปดํฌ๋ํธ์๋ ์ ํฌ๊ฐ ๋ณ๊ฒฝํ  number์ ๊ฐ์ ๋ณด์ฌ์ค๊ฒ์ด๋ฉฐ useContext(NumberContext)๋ฅผ ์ฌ์ฉํจ์ผ๋ก์จ value๊ฐ์ ์ ๊ทผ ํ  ์ ์๊ฒ ๋ฉ๋๋ค.

<br/>

### ๐ src>components>Button.jsx

---

<br/>

&nbsp; Button์ปดํฌ๋ํธ์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import React, { useContext } from "react";
import NumberContext from "../context/NumberContext";

const Button = () => {
  const { increase, decrease } = useContext(NumberContext);
  return (
    <div>
      <button onClick={increase}>+</button>
      <button onClick={decrease}>-</button>
    </div>
  );
};

export default Button;
```

<br/>

&nbsp; number๋ฅผ ๋ณ๊ฒฝํ  ๋ฒํผ ๋๊ฐ๋ฅผ ๊ฐ์ง๊ณ  ์์ผ๋ฉฐ useContext(NumberContext)๋ฅผ ์ฌ์ฉํจ์ผ๋ก์จ value๊ฐ์ ์ ๊ทผ ํ  ์ ์๊ฒ ๋ฉ๋๋ค.

<br/>

<p align="center"><img src="https://blog.kakaocdn.net/dn/cBHIpu/btq1zsIh4G2/kLkILYkDrMIZv3e4Mwd9k1/img.gif"/></p>

<br/>

&nbsp; ์ฌ๊ธฐ์ Context API์ ์ฅ์ ์ ๋์น ์ฑ์จ๋์? ๋ถ๋ช Header์ด๋ Button์ปดํฌ๋ํธ๋ ์๋ฌด props๋ฅผ ์ ๋ฌ ๋ฐ์ง ์์๋๋ฐ๋ state์ ๋ณํ๋ฅผ ์ฃผ๊ณ ์์ต๋๋ค.

<br/>

### ๐ src>context>ThemContext.js

---

<br/>

&nbsp; ์ด๋ฒ์ them์ state๋ฅผ ๋ณ๊ฒฝํด๋ณด๋๋ก ํ๊ฒ ์ต๋๋ค. ThemContext์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import { createContext } from "react";

const ThemContext = createContext({
  them: "light",
  onClick: () => {},
});

export default ThemContext;
```

<br/>

&nbsp; NumberContext์ ๊ตฌ์กฐ์ ๋ง์ฐฌ๊ฐ์ง๋ก createContext()๋ฅผ ์ฌ์ฉํ๊ณ  ๊ธฐ๋ณธ value๊ฐ์ ๊ฐ์ง๊ณ ์์ต๋๋ค.

<br/>

### ๐ src>provider>ThemProvider.js

---

<br/>

&nbsp; ThemProvider ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import React, { useState } from "react";
import ThemContext from "../context/ThemContext";

const ThemProvider = ({ children }) => {
  const onClick = () => {
    setThem((prevState) => {
      return {
        ...prevState,
        them: prevState.them === "light" ? "dark" : "light",
      };
    });
  };

  const init = {
    them: "light",
    onClick,
  };

  const [them, setThem] = useState(init);
  return <ThemContext.Provider value={them}>{children}</ThemContext.Provider>;
};

export default ThemProvider;
```

<br/>

&nbsp; ThemContext.Provider๋ฅผ ์ฌ์ฉํ์ฌ value๋ผ๋ props์ them์ ๋ด๊ณ ์์ผ๋ฉฐ them์ ์์์ ๋ช์ํ them, onClick๋ฅผ ๊ฐ์ง๊ณ ์์ต๋๋ค.

<br/>

### ๐ src>components>ThemBtn.jsx

---

<br/>

&nbsp; them์ state๋ฅผ ๋ณ๊ฒฝํ  ThemBtn์ปดํฌ๋ํธ์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import React, { useContext } from "react";
import ThemContext from "../context/ThemContext";

const ThemBtn = () => {
  const { onClick } = useContext(ThemContext);

  return <button onClick={onClick}>them</button>;
};

export default ThemBtn;
```

<br/>

&nbsp; useContext(ThemContext)๋ฅผ ์ฌ์ฉํจ์ผ๋ก์จ value๊ฐ์ ์ ๊ทผ ํ์ฌ onClick๋ฅผ ์ฌ์ฉํ๊ณ ์์ต๋๋ค.

<br/>

### ๐ src>components>Content.jsx

---

<br/>

&nbsp; ์ด๋ฒ์ them์ state์ ๋ฐ๋ผ ์์ด ๋ฐ๋ Content์๋๋ค.

<br/>

```js
import React from "react";
import ThemContext from "../context/ThemContext";

const Content = () => {
  return (
    <ThemContext.Consumer>
      {(ThemContext) => {
        const themStyle = {
          backgroundColor: ThemContext.them === "light" ? "#fff" : "#000",
          color: ThemContext.them === "light" ? "#000" : "#fff",
        };
        return (
          <article style={themStyle}>
            <h1>๊ฐ์ฌ</h1>
            <p>
              ๋๋ฆฌ๋ ๊ฝ๊ฐ๋ฃจ์ ๋์ด ๋ฐ๋ํด (์์ผ) ๋๋ฌผ์ด ๊ณ ์ฌ๋ ๊พน ์ฐธ์๋ ๋ด ๋ง์
              ํ์ผ  ๋น๋ฐ์ค๋ฐ ์ค๋ฅด๊ณจ์ ๋ฃ์ด๋๊ณ ์ ์์ํ ๋๊ฐ์ ์๊ฐ์ด๋๊น ์ฐ๋ฆฌ
              ๋์ ๋ง์ง๋ง ํ์ด์ง๋ฅผ ์ ๋ถํํด ์ด๋ ์๋ณ์ด ์ด๋ณด๋ค ์๋ฒฝํ ๊น Love me
              only till this spring ์ค ๋ผ์ผ๋ฝ ๊ฝ์ด ์ง๋ ๋  goodbye ์ด๋ฐ ๊ฒฐ๋ง์ด
              ์ด์ธ๋ ค ์๋ ๊ฝ์ ๊ฐ์ ์๋ ํ์ด์ ์ฐ๋ฆฌ ๋ด๋ ์ climax ์ ์ผ๋ง๋
              ๊ธฐ์ ์ผ์ด์ผ Ooh ooh Love me only till this spring ๋ด๋ฐ๋์ฒ๋ผ Ooh
              // ... ์ค๋ต
            </p>
          </article>
        );
      }}
    </ThemContext.Consumer>
  );
};

export default Content;
```

<br/>

&nbsp; ์ด์ ์ Header ์ปดํฌ๋ํธ์ ๊ฐ์ด ๋ณ๊ฒฝ๋ state๋ฅผ ๋ฐ์ ์ปดํฌ๋ํธ์ง๋ง ๋ค๋ฅธ์ ์ ๋์น ์ฑ์จ๋์? Header์ปดํฌ๋ํธ๋ useContext()๋ฅผ ์ด์ฉํ์ฌ value์ ๊ฐ์ ์ ๊ทผํ์์ง๋ง Content ์ปดํฌ๋ํธ๋ ๋ค๋ฆ๋๋ค. ThemContext.Consumer๋ฅผ ์ฌ์ฉํ์ฌ Provider์ value๊ฐ์ ๊ตฌ๋ํ๊ณ ์์ผ๋ฉฐ ๋ณ๊ฒฝ๋ state๋ฅผ ์์ฒด์ ์ผ๋ก ๋ฐ์์ ๋ฐฐ๊ฒฝ๊ณผ ํฐํธ์ ์์ ๋ณํ๋ฅผ ์ค๊ฒ์๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FeLHboy%2Fbtq1AEOXkq5%2FXcyaLeyCzBPS5M5zbabNCk%2Fimg.gif"/></p>

<br/>

&nbsp; Content ๋ํ ์์ ์ปดํฌ๋ํธ๋ก ๋ถํฐ ์ด๋ ํ props๋ฅผ ์ ๋ฌ ๋ฐ์ง ์์์์๋ state๋ฅผ ์๋ฐ์ดํธํ๊ณ  ๋ณ๊ฒฝ ๊ฐ์๋ฐ๋ฅธ ๋ณํ๋ฅผ ๋ณด์ฌ์ฃผ๊ณ ์์ต๋๋ค.

<br/>

<p align="center"><img src="https://blog.kakaocdn.net/dn/LHexh/btq1xlDamk1/pusrpjMD6ffA1hFe3utLak/img.png"/></p>

<br/>

&nbsp; ํ์ฌ ํ์ผ์ ๊ตฌ์กฐ๋ฅผ ์ฝ๊ฒ ๋ณด์๋ฉด ์์ ๊ฐ์ด ๋์ด์์ต๋๋ค. ๋ง์ฝ Context API๋ฅผ ์ฌ์ฉํ์ง ์๋๋ค๋ฉด App.js๋ถํฐ Them.jsx๊น์ง ๊ฐ๊ธฐ์ํด Page, Header ์ปดํฌ๋ํธ์ props๋ฅผ ์ ๋ฌ ํด์ผํ์ง๋ง Context API๋ฅผ ์ด์ฉํ์ฌ ๊ทธ๋ฌํ ๋ถํ์ํ ์์์ ํ์ง์์์ต๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fz8C3c%2Fbtq1uwrBbrI%2FrezUlpoQkpKaQ6krDkaVE1%2Fimg.png"/></p>

<br/>

&nbsp; ์์ ๊ฐ์ ํํ๋ก ๋ถํ์ํ props๋ฅผ ์ ๋ฌํ์ง ์๊ณ  ์ ์ญ์ํ ๊ด๋ฆฌ๋ฅผ ์ํด์๋ Context API๋ฅผ ํ์ฉํ์ฌ ์ดํ๋ฆฌ์ผ์ด์์ ์ค๊ณํ ์ ์์ต๋๋ค.

<br/>

[์ฐธ๊ณ ](https://reactjs.org/docs/context.html)

๐
