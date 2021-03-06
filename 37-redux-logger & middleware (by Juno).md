# 37-Redux-logger & Middleware

## ๐คทโโ๏ธ Middleware ๋?

<br/>

> Redux์์์ Middleware๋ ์ก์์ด ๋์คํจ์น(์คํ)๋์ด ๋ฆฌ๋์์์ ์ฒ๋ฆฌํ๊ธฐ์ ์ ์ง์ ๋ ์์๋ค์ ์๋ฏธํฉ๋๋ค.  
> ์ก์๊ณผ ๋ฆฌ๋์ ์ฌ์ด์ ์ค๊ฐ์๋ผ๊ณ ๋ ํ  ์ ์์ผ๋ฉฐ, ์ก์์ ์ฝ์์ ๊ธฐ๋กํ๊ณ  ์ก์์ทจ์, ๋ค๋ฅธ ์ข๋ฅ์ ์ก์์ ์ถ๊ฐ์ ์ผ๋ก ๋์คํจ์นํ  ์ ์์ต๋๋ค.
>
> Redux์ Middleware๋ Redux-Saga, Redux-thunk๊ฐ ์์ผ๋ ์ง์  ๋ง๋ค์ด๋ณด๋ฉฐ ๋์์ ๋ํ ์ดํด๋ฅผ ํด๋ด์๋ค.

<br/>

## ๐ ๊ตฌ์กฐ ์์๋ณด๊ธฐ

<br/>

&nbsp; ๋จผ์  Middleware๋ ์๋์ ๊ฐ์ ํํ๋ฆฟ์ ๊ฐ์ง๋๋ค.

<br/>

```js
const middleware = (store) => (next) => (action) => {
  // something working...
};
```

<br/>

&nbsp; ์์ ํํ๊ฐ ๋ํดํ๋ค๋ฉด function์ ํํ๋ก ๋ฐ๊ฟ๋ณด๊ฒ ์ต๋๋ค.

<br/>

```js
function middleware(store) {
  return function (next) {
    return function (action) {
      // something working...
    };
  };
}
```

<br/>

> **๐ก ์์ธํ ์์๋ณด๊ธฐ**
>
> - `store`๋ ๋ฆฌ๋์ค ์คํ ์ด ์ธ์คํด์ค์๋๋ค. `dispatch`, `getState`, `subscribe` ๋ด์ฅํจ์๊ฐ ์์ต๋๋ค.
> - `next`๋ ์ก์์ ๋ค์ ๋ฏธ๋ค์จ์ด์๊ฒ ์ ๋ฌํ๋ ํจ์์ด๋ฉฐ, `next(action)`ํํ๋ก ์ฌ์ฉํฉ๋๋ค. ๋ค์ ๋ฏธ๋ค ์จ์ด๊ฐ ์๋ค๋ฉด `reducer`์๊ฒ ์ก์์ ์ ๋ฌํฉ๋๋ค.
> - `action`์ ํ์ฌ ์ฒ๋ฆฌํ๊ณ  ์๋ ์ก์ ๊ฐ์ฒด ์๋๋ค.

<br/>

&nbsp; ๊ตฌ์กฐ๋ก ์์ ๋ณด์๋ฉด ์๋์ ๊ฐ์ต๋๋ค.

<br/>

<p align="center"><img src="https://miro.medium.com/max/2400/1*94LKNs35Z3GOZPhQ_Sd5qw.png"/></p>

<br/>

&nbsp; Middleware๋ ์ฌ๋ฌ ๊ฐ๋ฅผ ๋ฑ๋กํ  ์ ์์ต๋๋ค. ์ก์์ด ๋์คํจ์น(์คํ)๋๋ฉด ๋ฏธ๋ค์จ์ด๊ฐ ํธ์ถ๋๊ณ , Middleware์์ `next(action)`๋ฅผ ํธ์ถํ๊ฒ ๋๋ฉด ๋ค์ ๋ฏธ๋ค์จ์ด๋ ์ก์์ ์ ๋ฌํ๋ฉฐ ๋ง์ฝ ๋ฏธ๋ค์จ์ด์์ `store.dispatch`๋ฅผ ์ฌ์ฉํ๋ฉด ๋ค๋ฅธ ์ก์์ ์ถ๊ฐ์ ์ผ๋ก ๋ฐ์์ํต๋๋ค.

<br/>

## ๐ ์ฝ๋๋ก ์์๋ณด๊ธฐ

<br/>

&nbsp; ๋จผ์  Middleware ์์ฑ์ ์ํด ์์ ์ฝ๋๋ฅผ ์์ฑํด๋ณด๊ฒ ์ต๋๋ค.

<br/>

### ๐ src>middlewares>myLogger.js

---

<br/>

```js
const myLogger = (store) => (next) => (action) => {
  console.log(action); // ์ก์์ถ๋ ฅ
  const result = next(action); // ๋ค์ ๋ฏธ๋ค์จ์ด (๋๋ ๋ฆฌ๋์) ์๊ฒ ์ก์์ ๋ฌ
  console.log(store.getState());
  return result; //๋ฐํ๊ฐ์ dispatch(action)์ ๊ฒฐ๊ณผ๋ฌผ
};

export default myLogger;
```

<br/>

&nbsp; ๋ค์ Middleware ์ ์ฉํ๊ธฐ ์ํด ์คํ ์ด์ ์ ์ฉํฉ๋๋ค. ์ด๋ `applyMiddleware` ํจ์๋ฅผ ์ฌ์ฉํฉ๋๋ค.

<br/>

```js
import { applyMiddleware, createStore } from "redux";
import myLogger from "./middlewares/myLogger";

const init = {
  number: 0,
  diff: 1,
};

const reducer = (state = init, action) => {
  switch (action.type) {
    case "INCREASE":
      return { ...state, number: state.number + state.diff };
    case "DECREASE":
      return { ...state, number: state.number - state.diff };
    default:
      return state;
  }
};

const store = createStore(reducer, applyMiddleware(myLogger));

export default store;
```

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F2InOz%2Fbtq2MzUPegD%2F8WV6kMbkUciLMmK12431j1%2Fimg.gif"/></p>

<br/>

&nbsp; ์์ ๊ฐ์ด ๋ก๊น์ ํ๋ ์์์ ์ํด์๋ ์ง์  ๋ง๋๋ ๊ฒ ๋ณด๋จ redux-logger๋ฅผ ์ฌ์ฉํฉ๋๋ค.

<br/>

## ๐พ Redux-logger ์ํ ๋ฐ ์ฌ์ฉ

<br/>

&nbsp; ๋จผ์  Redux-logger๋ฅผ ์ค์นํฉ๋๋ค.

<br/>

```bash
yarn add redux-logger
```

<br/>

&nbsp; ์ดํ store์ ์ง์  ์์ฑํ๋ myLogger๋ ์ง์์ฃผ๊ณ  ์ค์นํ logger๋ฅผ ์ ์ฉํฉ๋๋ค.

<br/>

```js
import { applyMiddleware, createStore } from "redux";
import logger from "redux-logger";

const init = {
  number: 0,
  diff: 1,
};

const reducer = (state = init, action) => {
  switch (action.type) {
    case "INCREASE":
      return { ...state, number: state.number + state.diff };
    case "DECREASE":
      return { ...state, number: state.number - state.diff };
    default:
      return state;
  }
};

const store = createStore(reducer, applyMiddleware(logger));

export default store;
```

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcOu8il%2Fbtq2RjQwn1r%2FhzBmeab3rFo0nylDp6dYJ1%2Fimg.gif"/></p>

<br/>

&nbsp; ์์ ๊ฐ์ด ๋ก๊น์ ์ํ ์์์ด๋ผ๋ฉด redux-logger๋ฅผ ํตํ์ฌ ๊ฐ๋จํ๊ฒ ์ฌ์ฉํ  ์ ์์ต๋๋ค.

<br/>

[Redux DevTool ์ ์ฉํ๊ธฐ](https://react.vlpt.us/redux-middleware/03-logger-and-devtools.html)

๐
