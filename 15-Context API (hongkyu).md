###  ๐Context API๋ ๋ฌด์์ธ๊ฐ?



> 1. ํ๋ก์ ํธ ์์์ ์ํ, ๊ฐ, ํจ์ ๋ฑ์ ์ ์ญ์ ์ผ๋ก ์ฌ์ฉํ  ์ ์๊ฒ ํด์ค๋ค.
> 2. ์กฐ๋ถ๋ชจ ์ปดํฌ๋ํธ๋ก ๋ถํฐ ๊ฐ์ ์ ๋ฌ ๋ฐ๊ณ ์ ํ  ๊ฒฝ์ฐ, Props๋ฅผ ์ฌ์ฉํ๋ฉด ๋ถ๋ชจ์ปดํฌ๋ํธ๋ฅผ ๊ฒฝ์ ํด์ ๊ฐ์ ์ ๋ฌ๋ฐ์์ผ ํ๋ค. ํ์ง๋ง Context API๋ฅผ ์ฌ์ฉํ๋ฉด (๋ถ๋ชจ ์ปดํฌ๋ํธ๋ฅผ ๊ฒฝ์ ํ์ง ์๊ณ )์กฐ๋ถ๋ชจ๋ก ๋ถํฐ ์ง์  ์ ๋ฌ๋ฐ์ ์ ์๋ค.



![image](https://user-images.githubusercontent.com/75282888/113104241-439cb000-923b-11eb-98db-adceb36202a3.png)




๐ ์ฝ๋์๋๋ฐ์ค ์ฐธ์กฐํ๊ธฐ : https://codesandbox.io/s/stoic-glitter-v6xqj?file=/src/App.js




> ๐/src/App.js


```jsx

import React, { useState } from "react";
import Baby from "./Baby";
import "./styles.css";

export const UserContext = React.createContext(null);
//๐ React.createContext๋ฅผ ํธ์ถํ๊ณ 
//๐ ๋ฐํํ ๊ฐ์ export ํด์ค๋๋ค.
//๐ ์ด๋ ๊ฒ ํ๋ฉด UserContext.Provider๋ผ๋ ์ปดํฌ๋ํธ๋ฅผ ์์ฑํ  ์ ์์ต๋๋ค.

export default function App() {
  const [hearts, setHearts] = useState([]);
  const addHearts = (event) => {
    event.preventDefault();
    setHearts([...hearts, "๐"]);
  };
  return (
    <UserContext.Provider value={{ hearts, addHearts }}>
      {/* ๐ UserContext.Provider ์ปดํฌ๋ํธ๋ฅผ ๋ง๋ค๊ณ  */}
      {/* ๐ value ์์ฑ๊ฐ์ผ๋ก ์ ์ญ์ ์ผ๋ก ๊ด๋ฆฌํ๊ณ  ์ถ์ ๊ฐ์ ๋ฃ์ต๋๋ค.*/}
      {/* ๐ ๊ฐ, ๋ณ์, ์ํ, ํจ์ ๋ค ์ข์ต๋๋ค. */}
      {/* ๐ UserContext.Provider์ ์์(์์, ์กฐ์, ์ฆ์กฐ์, ๊ณ ์กฐ์ ๋ชจ๋!) ์ปดํฌ๋ํธ๋ค์  */}
      {/* ๋ชจ๋ value์์ฑ์ ์ ๋ฌ๋ ๊ฐ์ ์ ๊ทผํ  ์ ์์ต๋๋ค. */}
      <div>
        <p> - App - </p>
        <Baby />
      </div>
    </UserContext.Provider>
  );
}

```




> ๐/src/Baby.js

```jsx

import React from "react";
import BabyOfBaby from "./BabyOfBaby";
import "./styles.css";

export default React.memo(function Baby() {
  console.log("Baby๋ ๋์ฝ");
  return (
    <div>
      <p>- Baby -</p>
      <BabyOfBaby />
    </div>
  );
});

```


> ๐/src/BabyOfBaby.js



```jsx


import React, { useContext } from "react";
import "./styles.css";
import { UserContext } from "./App";
// ๐ App ์ปดํฌ๋ํธ์์ ์ ์ธํ๋ UserContext๋ฅผ Importํฉ๋๋ค.

export default function BabyOfBaby() {
  const context = useContext(UserContext);
  // ๐ useContextํจ์๋ฅผ ํธ์ถํ๊ณ  ์์ Importํ UserContetxt๋ฅผ ์ธ์๋ก ์ ๋ฌํฉ๋๋ค.
  // ๐ ์ด๋ ๊ฒํ๋ฉด useContextํจ์๋
  // ๐ App.js์ <UserContext.Provider>์ปดํฌ๋ํธ์ value์์ฑ๊ฐ์ ๋ฆฌํดํฉ๋๋ค.
  // ๐ ์ ํฌ๋ {hearts, addHearts} ๊ฐ์ฒด๋ฅผ value๊ฐ์ผ๋ก ๋ฃ์ด์คฌ์ง์?
  //
  console.log("BabyOfBaby ๋ ๋์ฝ");
  return (
    <div>
      <p>- BabyOfBaby -</p>
      <p>{context.hearts}</p>
      {/* ๐ App.js์์ ์์ฑํ ์ํ ํจ์ ๋ฑ์ ์ฌ์ฉํ  ์ ์์ต๋๋ค. */}
      <button onClick={context.addHearts}>ํํธ ์ถ๊ฐ</button>
    </div>
  );
}

```

