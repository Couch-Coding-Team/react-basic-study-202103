

## ๐น๐ CSS๋ง์ ์ฌ์ฉํ  ๋์ ๋ฌธ์ ์ 



React.js์์๋ ์ฑ ์ ์ฒด์ CSS๊ฐ ํ๋์ ๋ค์์คํ์ด์ค๋ฅผ ๊ณต์ ํ๋ค.  

์ฆ, ์๋ก ๋ค๋ฅธ ์ปดํฌ๋ํธ์์ import ๋์๊ณ ,  **<u>์๋ก ๋ค๋ฅธ CSSํ์ผ</u>**์์๋ 

<u>**์ค๋ณต๋ ํด๋์ค๋ค์์ ์ฌ์ฉํ  ๊ฒฝ์ฐ ์ถฉ๋์ด ๋ฐ์ํ๋ค.**</u>



์์๋ฅผ ๋ค์ด๋ณด๊ฒ ๋ค.



> ๐/src/Blue.css

```css
.box {
  font-family: sans-serif;
  text-align: center;
  background-color: aqua;
  height: 200px;
}

```

> ๐/src/Blue.jsx

```jsx
import "./Blue.css";

export default function Blue() {
  return (
    <div className="box">
      <h1>I am Blue</h1>
      <h2>bb</h2>
    </div>
  );
}

```




> ๐/src/Green.css

```css
.box {
  font-family: sans-serif;
  text-align: center;
  background-color: green;
  height: 200px;
}

```

> ๐/src/Green.jsx

```jsx
import "./Green.css";

export default function Green() {
  return (
    <div className="box">
      <h1>I am Green</h1>
      <h2>bb</h2>
    </div>
  );
}

```

![image](https://user-images.githubusercontent.com/75282888/113502723-1288ec00-9569-11eb-8c80-06f7ced612cc.png)

**\<Blue/>** ์ปดํฌ๋ํธ์๋ **Blue.css** ํ์ผ์ด, \**<Green/>** ์ปดํฌ๋ํธ์๋ **Green.css**ํ์ผ์ด ์ ์ฉ๋์๋ค. 

ํ์ง๋ง ๊ฐ์ ํด๋์ค๋ค์(.box)์ ์ฌ์ฉํ๋ค ๋ณด๋, ๊ฐ๊ฐ์ ์ปดํฌ๋ํธ์ ๋ค๋ฅธ ์คํ์ผ๋ง์ด ์ ์ฉ๋์ง ๋ชปํ์๋ค.

์ฆ, Blue.css์ .box์ Green.css์ .box๋ฅผ ๊ตฌ๋ถํ์ง ๋ชปํ๋ค๋ ์ด์ผ๊ธฐ๋ค.



์์) https://codesandbox.io/s/2021-04-01ihatecss-chnln





## ๐น๐ CSS Module๋ฅผ ํ์ฉํ ํด๋์ค์ด๋ฆ ์ค๋ณต ๋ฌธ์  ์๋ฐฉํ๊ธฐ



์ด๋ฌํ ๋ฌธ์ ๋ฅผ ํด๊ฒฐํ๊ธฐ ์ํด ์ฐ๋ฆฌ๋ CSS Module ๊ธฐ๋ฅ์ ํ์ฉํ  ์ ์๋ค.

CSS Module์ CSSํ์ผ๋ก๋ถํฐ ํด๋์ค๋ฅผ ๋ถ๋ฌ์์ ์ฌ์ฉํ ๋

\[ํ์ผ์ด๋ฆ]\_[ํด๋์ค์ด๋ฆ]\_[ํด์ฌ๊ฐ] ํํ๋ก <u>ํด๋์ค์ด๋ฆ์ ์๋์ผ๋ก **''์ ๋ํฌํ ๊ฐ''**์ผ๋ก ๋ง๋ค์ด์ค๋ค.</u>



CSS Module์ ์ฌ์ฉํ๊ธฐ ์ํด์๋

๋จผ์  ๊ธฐ์กด cssํ์ผ์ ํ์ฅ์๋ฅผ **.module.css** ๋ก ๋ณ๊ฒฝํด์ผ ํ๋ค.

> ๐/src/Blue.module.css

```css
.box {
  font-family: sans-serif;
  text-align: center;
  background-color: aqua;
  height: 200px;
}

```








> ๐/src/Blue.jsx

```jsx
import style from "./Blue.module.css";
//๐ ๊ทธ๋ฆฌ๊ณ  CSS Moduleํ์ผ์ "style"์ด๋ผ๋ ์ด๋ฆ์ผ๋ก importํ๋ฉด, style์ด๋ผ๋ ๊ฐ์ฒด๊ฐ ๋ง๋ค์ด์ง๋ค.
//๐ ๊ฐ๊ฐ์ ํด๋์ค๋ {style.ํด๋์ค๋ช} ํน์ {style['ํด๋์ค๋ช']} ์ผ๋ก ์ ๊ทผํ  ์ ์๋ค.
export default function Blue() {
  return (
    <div className={style.box}>
      <h1>I am Blue</h1>
      <h2>{style.box}</h2>
      {*/ Blue.module.css ํ์ผ์ .box ํด๋์ค๋ฅผ ์ฌ์ฉํ๊ณ  ์ถ๋ค๋ฉด/*}
      {*/ style.box๋ก ๋ถ๋ฌ์ฌ ์ ์๋ค. /*}

    </div>
  );
}


```




> ๐/src/Green.module.css

```css
.box {
  font-family: sans-serif;
  text-align: center;
  background-color: green;
  height: 200px;
}

```

> ๐/src/Green.jsx

```jsx
import styles from "./Green.module.css";

export default function Green() {
  return (
    <div className={styles.box}>
      <h1>I am Green</h1>
      <h2>{styles.box}</h2>
    </div>
  );
}


```

![image](https://user-images.githubusercontent.com/75282888/113503085-9ee7de80-956a-11eb-8edd-f290409b8c21.png)



์์)  https://codesandbox.io/s/2021-04-01ihatecssmodule-forked-exquw





## ๐น๐ classNames ๋ผ์ด๋ธ๋ฌ๋ฆฌ ํ์ฉํ๊ธฐ



> $ npm install classnames



ClassNames๋ CSS ํด๋์ค๋ฅผ **<u>์กฐ๊ฑด๋ถ</u>**๋ก ์ค์  ํ  ๋ ๋งค์ฐ ์ ์ฉํ ๋ผ์ด๋ธ๋ฌ๋ฆฌ์ด๋ค.

์๋์ ๊ฐ์ด ํน์  Class๋ฅผ **{ํด๋์ค ์ด๋ฆ : boolean}** ์ผ๋ก ์ค์ ํ๋ฉด,

true, false ์ฌ๋ถ์ ๋ฐ๋ผ ํด๋น ํด๋์ค๋ฅผ ๋ฐ์์ํฌ ์ ์๋ค.

> ์์

```jsx	
import classNames from 'classnames';

classNames('one', 'two'); // 'one two'
classNames('one', { two: true }); // 'one two'
classNames('one', { two: false }); // 'one'
classNames('one', ['two', 'three']); // 'one two three'

const myClass = 'hello';
classNames('one', myClass, { myCondition: true }); //'one hello myCondition'

const MyComponent = ({ highlighted, theme }) => {
  <div className={classNames('MyComponent', { highlighted }, theme)}>Hello</div>
} //highlighted ์ธ์์ ์ ๋ฌ๋๋ ๊ฐ์ด true์ด๋ฉด 
//div์ ํด๋์ค ๋ค์์ผ๋ก {classNames('MyComponent', { highlighted : true }, theme)}์ด ์ ๋ฌ๋  ๊ฒ์ด๋ค.
//๊ทธ๋ฆฌ๊ณ  them ์ธ์์ ์ ๋ฌ๋๋ ๋ฌธ์์ด์ด div์ ํด๋์ค๋ก ์ถ๊ฐ๋  ๊ฒ์ด๋ค.


```









## ๐น๐ classNames ๐ CSS Module 



์ถ๊ฐ์ ์ผ๋ก, CSS Module๊ณผ classNames๋ฅผ ํจ๊ป ํ์ฉํ  ์๋ ์๋ค. 

ํนํ **classNames.bind()** ๋ฉ์๋๋ฅผ ์ด์ฉํ๋ฉด, <u>์ฌ๋ฌ ํด๋์ค๋ฅผ ๋์์ ์ ์ฉ</u>์ํฌ ๋ ๋ณด๋ค ํธํ๊ฒ ์์ฑํ  ์ ์๋ค.

```jsx
import React from 'react';
import classNames from 'classnames/bind';
import styles from './CSSModule.module.css';

const cx = classNames.bind(styles); // ๋ฏธ๋ฆฌ styles ์์ ํด๋์ค๋ฅผ ๋ฐ์์ค๋๋ก ์ค์ ํ๊ณ 

const CSSModule = () => {
  return (
    <div className={cx('wrapper', 'inverted')}> 
          {*/์ด๋ ๊ฒ ํ๋ฉด ๊ธฐ์กด CSS Module ๊ธฐ๋ฅ๋ง ํ์ฉํ๋ ๊ฒ๋ณด๋ค ๊ฐ๊ฒฐํ ์ฝ๋ ์์ฑ์ด ๊ฐ๋ฅํด์ง๋ค./*}
          {*/ ๊ธฐ์กด ๋ฐฉ์ : {styles.wrapper} {styles.inverted}/*}

      ์๋ํ์ธ์, ์ ๋ <span className="something">CSS Module!</span>
    </div>
  );
};

export default CSSModule;

```



์์ ) https://codesandbox.io/s/2021-04-01ihatecssmodule-grdsj
