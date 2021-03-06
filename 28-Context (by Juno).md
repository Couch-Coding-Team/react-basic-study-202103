# 28-Context

## ๐ API์ Context ์ฐ๋ํ๊ธฐ

<br/>

> Axios๋ฅผ ์ด์ฉํ์ฌ API๋ฐ์ดํฐ๋ฅผ ๋ก๋์ Context API๋ก ์ํ๊ด๋ฆฌ๋ฅผ ํ์ฉํ์ฌ ๋ด์๋ค.

<br/>

### ๐ ์ฝ๋๋ก ์์๋ณด๊ธฐ

---

<br/>

&nbsp;์ ์ฒด์ ํ์ผ ๊ตฌ์กฐ๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdfp75X%2Fbtq11LVWTkj%2FMbqhG7UMX1y1MYiKFKtD31%2Fimg.png"/></p>

<br/>

### ๐ src>App.js

---

<br/>

&nbsp;ํ์คํธ๋ฅผ ์ํ์ฌ App.js์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import DataProvider from "./Provider/DataProvider";

const App = () => {
  return (
    <>
      <Header />
      <DataProvider>// ...</DataProvider>
      <Footer />
    </>
  );
};

export default App;
```

<br/>

### ๐ src>context>DataContext.js

---

<br/>

&nbsp; DataContext ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import { createContext } from "react";
const DataContext = createContext({
  state: "init",
  handleState: () => {},
});

export default DataContext;
```

<br/>

&nbsp; createContext()๋ฅผ ์ฌ์ฉํ์๊ณ  ๊ธฐ๋ณธ value๋ค์ ๊ฐ์ง๊ณ ์์ต๋๋ค.

<br/>

### ๐ src>provider>DataProvider.js

---

<br/>

&nbsp; DataProvider ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import React, { useState } from "react";
import DataContext from "../context/DataContext";

const DataProvider = ({ children }) => {
  const handleState = (state) => {
    setState((prevState) => {
      return {
        ...prevState,
        state,
      };
    });
  };

  const init = {
    state: "init",
    handleState,
  };

  const [state, setState] = useState(init);

  return <DataContext.Provider value={state}>{children}</DataContext.Provider>;
};

export default DataProvider;
```

<br/>

&nbsp; createContext()๋ฅผ ์ฌ์ฉํ์๊ธฐ๋๋ฌธ์ DataContext.Provider๋ฅผ ์ฌ์ฉ ํ  ์ ์๊ฒ ๋์๊ณ  value๋ผ๋ props์ state๋ฅผ ๋ด๊ณ ์์ผ๋ฉฐ state๋ ์์์ ๋ช์ํ state, handleState๋ฅผ ๋ด๊ณ ์์ต๋๋ค.

<br/>

### ๐ src>components>KoreaData>KoreaAllData>KoreaAllData.jsx

---

<br/>

&nbsp; KoreaAllData์ปดํฌ๋ํธ์ ์ฝ๋๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```js
import DataContext from "../../../context/DataContext";

const KoreaAllData = () => {
  const { state, handleState } = useContext(DataContext);
  const [isLoading, setIsLoading] = useState(true);

  //... ์ค๋ต

  useEffect(() => {
    //... ์ค๋ต

    axios
      .get("https://projectgoc.herokuapp.com/api")
      .then((res) => {
        const data = res.data.elements[0].elements[1].elements[0].elements;
        const items = data.slice(0, 133);
        const totalData = items[18].elements;
        const yesterDayData = items[37].elements;
        panelDataHandler(totalData);
        cardsDataHandler(totalData, yesterDayData);
        chartDataHandler(items);
        setIsLoading(false);
        handleState("success");
      })
      .catch((err) => {
        handleState("false");
        console.log(err);
      });
  }, [state]);

  return (
    <DataContext.Consumer>
      {(DataContext) => {
        return (
          <>
            {DataContext.state != "false" ? (
              <>{isLoading ? <Loading /> : <>//... ์ค๋ต</>}</>
            ) : (
              <Err />
            )}
          </>
        );
      }}
    </DataContext.Consumer>
  );
};

export default KoreaAllData;
```

<br/>

&nbsp; ํด๋น ์ปดํฌ๋ํธ๋ Axios๋ฅผ ์ด์ฉํ์ฌ ๊ณต๊ณต๋ฐ์ดํฐํฌํธ์ API๋ฅผ ์ฌ์ฉํ์ฌ ๋ฐ์ดํฐ๋ฅผ ๋ก๋ํ๊ณ  ์์ผ๋ฉฐ, ์ฑ๊ณต์ ํ๊ฒ๋๋ฉด handleState์ success๋ฅผ ์ ๋ฌํ๊ณ  ์คํจ์ false๋ฅผ ์ ๋ฌํ๊ฒ ๋ฉ๋๋ค. ๋ ์ด ์ปดํฌ๋ํธ๋ DataContext.Consumer๋ฅผ ์ฌ์ฉํ์ฌ DataContext์ ์ํ๋ฅผ ๊ตฌ๋ํ๊ณ  ์๊ธฐ ๋๋ฌธ์ ๊ทธ์ ๋ฐ๋ฅธ ๊ฒฐ๊ณผ๋ฅผ ๋ณด์ฌ์ฃผ๊ฒ ๋ฉ๋๋ค.

<br/>

๐
