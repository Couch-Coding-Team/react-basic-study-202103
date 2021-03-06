# 9-useEffect

## ๐ useEffect๋?

<br/>

> class Component์ lifecycle์ฒ๋ผ functional Component์์ Hook์ ์ฌ์ฉํ์ฌ ํน์  ์ํฉ์ ์์ ์ฒ๋ฆฌ๋ฅผ ๊ฐ๋ฅํ๋๋ก ํด์ค๋๋ค.

<br/>

## 3-1 class Component lifecycle

<br/>

&nbsp; ๋จผ์  ์๋์ ์ผ๋ก ์ ์ฌ์ฉํ์ง๋ ์์ง๋ง ์ดํด๋ฅผ ์ํด class Component์ lifecycle๋ฅผ ์์๋ณด๊ฒ ์ต๋๋ค.

<br/>

<p align="center"><img src="https://gseok.gitbooks.io/react/content/assets/react-life-cycle-2.png"/></p>

<br/>

&nbsp; ์ฌ์ง์์ ์ถ๊ฐ์ ์ผ๋ก React 17.0๋ฒ์  ์ดํ componentWillMount()์ componentWillUpdate()๋ ํ๊ธฐ๋์์ต๋๋ค.

<br/>

### ๐ ์ฝ๋๋ก ์์๋ณด๊ธฐ

---

<br/>

&nbsp;์ ์ฒด์ ํ์ผ ๊ตฌ์กฐ๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FqqxJT%2Fbtq1bfJE9bV%2FBFF7KEM5rcG3Ls8WwLHGD1%2Fimg.png"/></p>

### ๐ src>App.js

---

<br/>

&nbsp;ํ์คํธ๋ฅผ ์ํ์ฌ App.js์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import { useState } from "react";
import "./App.css";
import AdvancedFunction from "./components/AdvancedFunction";
import ClassComponents from "./components/ClassComponents";
import FunctionComponents from "./components/FunctionComponents";

function App() {
  const [mode, setMode] = useState("classComponent");
  const [classComponent, setClassComponent] = useState(true);
  const [functionComponent, setFunctionComponent] = useState(null);
  const [advancedFunction, setAdvancedFunction] = useState(null);

  return (
    <>
      <h1>ํ์ฌ {mode} ์ปดํฌ๋ํธ ์๋๋ค.</h1>
      <div>
        <button
          type="button"
          onClick={() => {
            setMode("classComponent");
            setClassComponent(true);
            setFunctionComponent(null);
            setAdvancedFunction(null);
          }}
        >
          View ClassComponent
        </button>
        <button
          type="button"
          onClick={() => {
            setMode("functionComponent");
            setClassComponent(null);
            setFunctionComponent(true);
            setAdvancedFunction(null);
          }}
        >
          View FunctionComponent
        </button>
        <button
          type="button"
          onClick={() => {
            setMode("advancedFunction");
            setClassComponent(null);
            setFunctionComponent(null);
            setAdvancedFunction(true);
          }}
        >
          View AdvancedFunction
        </button>
      </div>
      {classComponent && <ClassComponents />}
      {functionComponent && <FunctionComponents />}
      {advancedFunction && <AdvancedFunction />}
    </>
  );
}

export default App;
```

<br/>

### ๐ src>components>ClassComponents.jsx

---

<br/>

&nbsp;๋จผ์  ClassComponents์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import React, { Component } from "react";

class ClassComponents extends Component {
  constructor(props) {
    super(props);
    this.state = {
      number: 1,
    };
  }
  // componentWillMount() {
  // ํ๊ธฐ
  // }
  componentDidMount() {
    document.title = "index.html";
    console.log("ํ๋ฉด์ด ๊ทธ๋ ค์ง๊ณ  ๋ ํ", this.state.number);
  }
  shouldComponentUpdate(nextProps, nextState) {
    console.log("-------------------์ํ ์๋ฐ์ดํธ ๊ฐ์ง", this.state.number);
    return true;
  }
  // componentWillUpdate() {
  // ํ๊ธฐ
  //   getSnapshotBeforeUpdate() ์ผ๋ก ๋์ฒด
  // }
  componentDidUpdate() {
    console.log("์๋ฐ์ดํธ ์๋ฃ", this.state.number);
  }
  render() {
    console.log("ํ๋ฉด ๊ทธ๋ ค์ง", this.state.number);
    return (
      <div>
        <h2>ํด๋์ค ์ปดํฌ๋ํธ </h2>
        <span>{this.state.number}</span>
        <button
          type="button"
          onClick={() => {
            this.setState({ number: this.state.number + 1 });
          }}
        >
          CLICK โ
        </button>
      </div>
    );
  }
}

export default ClassComponents;
```

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FxnVoB%2Fbtq09yQTGfD%2F52pXHEjjhu352CrJlgaU70%2Fimg.png"/></p>

<br/>

&nbsp;ํ์ฌ๋ componentWillMount()๋ ํ๊ธฐ๊ฐ ๋์๊ธฐ๋๋ฌธ์ ๋ ๋๋ง์ด ๋๋ฉด render() -> componentDidMount() ์์ผ๋ก ์คํ์ด ๋ฉ๋๋ค.

- ์ฐธ๊ณ ๋ก componentWillUpdate()๋ getSnapshotBeforeUpdate()๋ก ๋์ฒด๋์์ต๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcWSMPI%2Fbtq1dy20AHQ%2FDVhVTQcTbrYy3T1m8mpsr1%2Fimg.png"/></p>

<br/>

&nbsp;์ด๋ ๋ฒํผ์ ํด๋ฆญํ์ฌ number์ ๊ฐ์ ์ฆ๊ฐ์์ผ๋ณด๊ฒ ์ต๋๋ค.

<br/>

<p align="center"><img src="https://blog.kakaocdn.net/dn/3U64w/btq1bfJGbpM/gwWFuVUJjCfletyGvfVNh0/img.gif"/></p>

<br/>

&nbsp;๋ฒํผ์ ํด๋ฆญํ์ฌ setState์ state๊ฐ ๋ณ๊ฒฝ๋๋ฉด shouldComponentUpdate()๊ฐ ๋จผ์  ์คํ์ด๋๊ณ  true๋ฅผ ๋ฆฌํดํ๊ณ  ์๊ธฐ ๋๋ฌธ์ render()๋ฅผ ๋ค์ ์คํํ๊ณ  componentDidUpdate()๋ฅผ ์คํํ๊ฒ ๋ฉ๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FuQaxE%2Fbtq1aQDkDcE%2FJfk1IxZxGbTtlCbde13nI1%2Fimg.png"/></p>

<br/>

## 3-2 functional Component with Hooks

<br/>

&nbsp;์์์ ์์๋ณธ class Component์ lifecycle์ฒ๋ผ functional Component์์๋ Hooks๋ฅผ ์ด์ฉํ์ฌ ์์์ด ๊ฐ๋ฅํฉ๋๋ค.

> ๐ก React 16.8 ์ดํ์ React-Hooks์์๋ useEffect ๋ฟ๋ง์๋ ์ํ๊ด๋ฆฌ, ์ฑ๋ฅ๋ฑ์ Hooks API๋ฅผ ์ ๊ณตํ๊ณ  ์์ต๋๋ค.  
>  [React-Hooks APIs] (https://reactjs.org/docs/hooks-reference.html)

<br/>

### ๐ ์ฝ๋๋ก ์์๋ณด๊ธฐ

---

<br/>

### ๐ src>components>FunctionComponents.jsx

---

<br/>

&nbsp;Hooks์์๋ useEffect()๋ฅผ ์ฌ์ฉํ๋ฉด lifecycle๋ฅผ ๊ด๋ฆฌํ  ์ ์์ผ๋ฉฐ componentDidMount(), componentDidUpdate(), componentWillUnmount()์ ๊ธฐ๋ฅ์ ์ฌ์ฉํ๊ณ  ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

> ๐ก useEffect() ๊ตฌ์กฐ ์์๋ณด๊ธฐ  
> ๋ค์ด๊ฐ๊ธฐ์  useEffect()์ ๊ธฐ๋ณธ ๊ตฌ์กฐ๋ฅผ ๋ณด์๋ฉด
>
> > ```js
> > useEffect(effect: EffectCallback, deps?: DependencyList)
> > ```
>
> ์์ ๊ฐ์ ๊ตฌ์กฐ๋ก ๋์ด์์ต๋๋ค.  
> ์ฒซ๋ฒ์งธ ์ธ์๊ฐ์ผ๋ก๋ ์คํํ  ์ฝ๋ฐฑํจ์, ๋๋ฒ์งธ ์ดํ์๋ ์์กด์ฑ์ ์ํ deps๊ฐ์ ๋ฃ๊ฒ ๋์ด์์ต๋๋ค.
>
> React์์๋ useEffect์์์ ์ฌ์ฉ๋๋ ์ํ๋ props๊ฐ ์๋ค๋ฉด deps์ ๋ฃ์ด์ค์ผํ๋๊ฒ ๊ท์น์๋๋ค.  
> ๋ง์ฝ deps๋ฅผ ๋ฃ์ง ์๋๋ค๋ฉด ํจ์๊ฐ ์คํ๋  ๋ ์ต์ ์ ์ํ๋ฅผ ๊ฐ๋ฅดํค์ง ์๊ฒ๋ฉ๋๋ค. (์์กด์ฑ)
>
> ์ด ๊ธฐ๋ณธ ๊ตฌ์กฐ๋ฅผ ์ ๊ธฐ์ตํ์๊ณ  ์๋์ ๋ด์ฉ์ ์ด์ด๋๊ฐ์๊ธธ ๋ฐ๋๋๋ค.

<br/>

```js
import React, { useEffect, useState } from "react";

const FunctionComponents = () => {
  const [number, setNumber] = useState(1);

  useEffect(() => {
    console.log("---------FunctionComponents");
    console.log("componentDidMount & componentDidUpdate");
    console.log("์ซ์ ์ค์  ๋จ", number);
    document.title = number;
    return () => {
      console.log("---------- cleanup ");
      console.log("์ซ์ ๋ณ๊ฒฝ ์ ", number);
    };
  }, [number]);

  const onNumber = () => {
    setNumber((number) => number + 1);
  };

  return (
    <div>
      <h2>ํจ์ํ ์ปดํฌ๋ํธ </h2>
      <span>{number}</span>
      <button type="button" onClick={onNumber}>
        CLICK โ
      </button>
    </div>
  );
};

export default FunctionComponents;
```

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdTwlIF%2Fbtq1e8pu32H%2FAPZ3pdfwGs0kVkcDbYflt0%2Fimg.png"/></p>

<br/>

&nbsp;๊ธฐ๋ณธ์ ์ผ๋ก ๋ ๋๋ง์ด ๋  ์์๋ return์ด์ ์ ์ฝ๋๋ฅผ ์คํํฉ๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdPJzNM%2Fbtq1g9aEbiu%2Fg0TTvv1zyOnYQXHsugDYrk%2Fimg.png"/></p>

<br/>

&nbsp;์ฌ๊ธฐ์ ๋ฒํผ์ ํด๋ฆญํ์ฌ setNumber์ state๋ฅผ ์๋ฐ์ดํธ ํด๋ณด๊ฒ ์ต๋๋ค.

<br/>

<p align="center"><img src="https://blog.kakaocdn.net/dn/TRiqm/btq1beKLmWU/vQhGbYdVRnpV2TLPxoFPN1/img.gif"/></p>

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F1e1Cb%2Fbtq1aRWBOLd%2F16ydCudSPzuuOcpJl9XGxK%2Fimg.png"/></p>

<br/>

&nbsp;useEffect()๋ state์ ๋ณํ๊ฐ ์๊ฒจ ๋ฆฌ๋ ๋๋ง์ ์ํฉ์ด ๋๋ฉด ์๋ฐ์ดํธ๊ฐ ๋๊ธฐ์  ๋ด๋ถ์ return์ด ์๋ค๋ฉด ๋จผ์  ์คํ์ด ๋ฉ๋๋ค. ์ด๋ return์ ํจ์๋ฅผ ๋ฆฌํดํด์ผํ๋ฉฐ clean-up ํจ์๋ผ๊ณ  ํฉ๋๋ค.

<br/>

> ๐ก clean-up ํจ์๋?  
> useEffect()์์ EffectCallback์ returnํจ์์๋๋ค.  
> component์ Unmount/Update์ ์์์ ํ๊ธฐ์  ์ํํ๋ ค๋ ํจ์๋ฅผ ๋งํฉ๋๋ค.  
> ์๋ต์ด ๊ฐ๋ฅํ๋ ๋ง์ฝ clean-upํจ์๋ฅผ ์ฌ์ฉํ๋ฉด clean-up ์คํ -> render -> EffectCallback์ ์์๋ก ์คํ๋ฉ๋๋ค.

<br/>

## ๐ ํ์ฉํ๊ธฐ

<br/>

&nbsp;๊ทธ๋ผ useEffect()๋ฅผ ์ด๋ป๊ฒ ํ์ฉํ๋ฉด ์ข์์ง ์์๋ณด๊ฒ ์ต๋๋ค.

<br/>

### ๐ ์ฝ๋๋ก ์์๋ณด๊ธฐ

---

<br/>

### ๐ src>components>AdvancedFunction.jsx

---

<br/>

&nbsp; ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

> **๐ Key Point**  
> useEffect()๋ deps์ ํ๋ผ๋ฏธํฐ ๊ฐ๋ค์ด ์๋ฐ์ดํธ ๋์๋ componentDidUpdate() ์ฒ๋ผ ์คํ๋ฉ๋๋ค.  
> ์ปดํฌ๋ํธ์์ ๊ฐ๊ฐ์ state๋ณํ์๋ฐ๋ผ ์ด๋ป๊ฒ ์คํ๋๋์ง ์์๊ฐ์๊ธธ ๋ฐ๋๋๋ค.

<br/>

```js
import React, { useEffect, useState } from "react";

const AdvancedFunction = () => {
  const [number, setNumber] = useState(1);
  const [date, setDate] = useState(new Date().toString());

  useEffect(() => {
    console.log("์ซ์ ์ค์  ๋จ", number);
    return () => {
      console.log("cleanup");
      console.log("์ซ์ ๋ณ๊ฒฝ ์ ", number);
    };
  }, [number]);

  useEffect(() => {
    console.log("๋ ์ง ์ค์  ๋จ", date);
    document.title = date;
    return () => {
      console.log("๋ ์ง ๋ณ๊ฒฝ ์ ", date);
    };
  }, [date]);

  const onNumber = () => {
    setNumber((number) => number + 1);
  };
  const onDate = () => {
    setDate(new Date().toString());
  };

  return (
    <div>
      <h2>ํ์ฉ ํ๊ธฐ</h2>
      <div>
        <h3>์ซ์ ๋ณ๊ฒฝ </h3>
        <span>{number}</span>
        <button type="button" onClick={onNumber}>
          CLICK โ
        </button>
      </div>
      <div>
        <h3>๋ ์ง ๋ณ๊ฒฝ </h3>
        <span>{date}</span>
        <button type="button" onClick={onDate}>
          CLICK โ
        </button>
      </div>
    </div>
  );
};

export default AdvancedFunction;
```

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FekEUNg%2Fbtq091rSS6q%2FMxEksEwnW9g3kDflTCVUzk%2Fimg.png"/></p>

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcQ8g6t%2Fbtq1aSusANE%2FB1BkwcuAqOhj82KnjuMuaK%2Fimg.png"/></p>

<br/>

&nbsp;์ปดํฌ๋ํธ๊ฐ ๋ ๋๋ง ๋๋ ๋๊ฐ์ useEffect()๊ฐ ์คํ๋๊ฑธ ํ์ธ ํ์์ต๋๋ค.  
์ฌ๊ธฐ์ ์ซ์ ๋ณ๊ฒฝ ๋ฒํผ์ ๋จผ์  ํด๋ฆญ ํด๋ณด๊ฒ ์ต๋๋ค.

<br/>

<p align="center"><img src="https://blog.kakaocdn.net/dn/FMlVR/btq09ypXbIY/bdTV2Y7JOvsCZxWV4ir6l0/img.gif"/></p>

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fn297o%2Fbtq1dAs4ip6%2FUHPMSQvIXbgpVcSMATOY2k%2Fimg.png"/></p>

<br/>

&nbsp;์์ ๊ฐ์ด setNumber()์ state๋ง ๋ณ๊ฒฝ์ด ๋๋ number์ deps๋ฅผ ๊ฐ์ง useEffect()๋ง ์คํ ๋์์ต๋๋ค.  
์ด๋ฒ์ ๋ ์ง ๋ณ๊ฒฝ ๋ฒํผ์ ํด๋ฆญ ํด๋ณด๊ฒ ์ต๋๋ค.

<br/>

<p align="center"><img src="https://blog.kakaocdn.net/dn/bDrcz5/btq1e6yvHMR/n1KCdp0veZLhJTsbEMBBe1/img.gif"/></p>

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F4bZYu%2Fbtq0916wBUu%2F78KKe3tykSxpELqRK3OGak%2Fimg.png"/></p>

<br/>

&nbsp;์ด์ฒ๋ผ useEffect()๋ ๊ฐ์ง๊ณ ์๋ ํด๋น deps์ ๋ณํ์๋ง ๋ง์ถฐ์ ์ฌ์ฉ์ด ๊ฐ๋ฅํฉ๋๋ค.

<br/>

> **๐ก Bonus**  
> [] ๋น ๋ฐฐ์ด๋ง ๋ฃ์ผ๋ฉด componentDidMount๋ก๋ง ์ฌ์ฉ์ด ๊ฐ๋ฅํ๋ค
> ๋์ค []๋ฅผ ์๋ตํ๊ฒ ๋๋ฉด ๋ฐ์ดํฐ ํ์นญ์ ํ ๋ ๋ฌดํ๋ฃจํ์ ๋น ์ง๋๋ฐ ์ด๊ฒ ์์ผ๋ฉด ๋งค ๋ ๋๋ง๋ค ์คํ๋๊ธฐ ๋๋ฌธ์

<br/>

&nbsp;๋ง์ฝ ์ปดํฌ๋ํธ๊ฐ Unmount ๋ ๋์ ์ฒ๋ฆฌ๋ฅผ ์ํด์๋ ์ด๋ป๊ฒ ํด์ผํ ๊น์?

๐
