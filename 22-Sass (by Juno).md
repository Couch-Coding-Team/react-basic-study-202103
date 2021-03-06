# 22-Sass

## ๐ Sass(**Syntactically Awesome** Style Sheets)?

<br/>

> Sass๋ CSS pre-processor๋ก์, ๋ณต์กํ ์์์ ์ฝ๊ฒ ํ  ์ ์๊ฒ ํด์ฃผ๊ณ , ์ฝ๋์ ์ฌํ์ฉ์ฑ๊ณผ ๊ฐ๋์ฑ์ ๋์ฌ์ค๋๋ค.

<br/>

> ๐ก CSS pre-processor(CSS ์ ์ฒ๋ฆฌ๊ธฐ) ?
>
> CSS๋ฅผ ํ์ฅํ๋ ์คํฌ๋ฆฝํ ์ธ์ด๋ก์, ์ปดํ์ผ๋ฌ๋ฅผ ํตํ์ฌ ๋ธ๋ผ์ฐ์ ์์ ์ฌ์ฉ ํ  ์ ์๋ ์ผ๋ฐ CSS ๋ฌธ๋ฒ ํํ๋ก ๋ณํํฉ๋๋ค.
>
> Sass, Less, PostCSS, Stylus etc...

<br/>

## 1. ๐พ ์ํํ๊ธฐ

<br/>

&nbsp; Sass๋ฅผ ์ฌ์ฉํ๊ธฐ์ํด node-sass๋ฅผ ์ค์นํฉ๋๋ค.

<br/>

```bash
yarn add node-sass
```

<br/>

&nbsp; ์ดํ Sass๋ฅผ ์ฌ์ฉํ๊ธฐ์ํด cssํ์ผ์ ํ์ฅ์๋ช์ .scss๋ฅผ ์ฌ์ฉํ์ฌ ์์ฑํฉ๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Ft4zLY%2Fbtq1JANybVD%2FprnbSgGPNPaMstmksO3DX0%2Fimg.png"/></p>

<br/>

> ๐ก .sass ์ .scss  
>  Sass๊ฐ ์ฒ์ ๋ฆด๋ฆฌ์ฆ ๋์์๋๋ .sassํ์ฅ์๋ก CSS์ ๋ฌธ๋ฒ์ด ๋ง์ด ๋ฌ๋์ต๋๋ค.  
> ๋๋ฌธ์ Sass๋ฒ์  3์ด์๋ถํฐ๋ ์ฃผ ๋ฌธ๋ฒ์ผ๋ก .scss๋ก ๋ณ๊ฒฝ๋์์ต๋๋ค.  
> .scss๋ .css์ ์์ ์งํฉ์ผ๋ก css์ ๋์ผํ ๋ฌธ๋ฒ์์ Sass์ ํน๋ณํ ๊ธฐ๋ฅ์ด ์ถ๊ฐ๋์์ต๋๋ค.

<br/>

## 2. ๐ ์ดํด๋ณด๊ธฐ

<br/>

### 2-1. Comment (์ฃผ์)

<br/>

&nbsp; .scss๋ด๋ถ์์ ์ฃผ์์ ํ  ๊ฒฝ์ฐ ํ์ค ์ฃผ์์ `//`๋ก ํ๊ธฐํฉ๋๋ค.

<br/>

```scss
/*This is comment*/

// This is comment

/*
This
is
comment
*/
```

<br/>

```css
/*This is comment*/

/*
This
is
comment
*/
```

<br/>

### 2-2. Variable (๋ณ์)

---

<br/>

&nbsp; Sass์์ ๋ณ์์ ๊ฐ๋์ ์ฌ์ฉํ  ์ ์์ต๋๋ค. ์ํ๋ ๋ณ์๋ช์ ์์ `$`๋ฌธ์๋ฅผ ์ฌ์ฉํฉ๋๋ค.

<br/>

```scss
/* Sass */
$personal: #369fff;

.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: $personal;
  border-radius: 3px;
  border: 0;
  outline: 0;
}
```

<br/>

```css
/* css */
.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: #369fff;
  border-radius: 3px;
  border: 0;
  outline: 0;
}
```

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb2uqd5%2Fbtq1JWJzWjF%2FBEBOzTPpNkJczUOxKgi7bk%2Fimg.png"/></p>

<br/>

#### 2-2-1. Variable Scope (๋ณ์ ๋ฒ์)

---

<br/>

&nbsp; Sass์ ๋ณ์๋ javascript์ ๋ง์ฐฌ๊ฐ์ง๋ก Block Scope๋ฅผ ์ฌ์ฉํฉ๋๋ค.

<br/>

```scss
/* Sass */
$personal: #369fff;

.btn {
  $personal: #000;
  padding: 5px 20px;
  color: #fff;
  background-color: $personal;
  border-radius: 3px;
  border: 0;
  outline: 0;
}

.p {
  color: $personal;
}
```

<br/>

```css
/* css */
.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: #000;
  border-radius: 3px;
  border: 0;
  outline: 0;
}

.p {
  color: #369fff;
}
```

<br/>

#### 2-2-2. Variable Scope (!global)

---

<br/>

&nbsp; Block Scope๋ด์์ ๋ณ์๋ฅผ ์ ์ธํ๋๋ผ๋ `!global` ํ๋๊ทธ๋ฅผ ์ฌ์ฉํ๋ฉด ์ ์ญ์์ ์ฌ์ฉ์ด ๊ฐ๋ฅํฉ๋๋ค.

<br/>

```scss
/* Sass */
$personal: #369fff;

.btn {
  $personal: #000 !global;
  padding: 5px 20px;
  color: #fff;
  background-color: $personal;
  border-radius: 3px;
  border: 0;
  outline: 0;
}

.p {
  color: $personal;
}
```

<br/>

```css
/* css */
.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: #000;
  border-radius: 3px;
  border: 0;
  outline: 0;
}

.p {
  color: #000;
}
```

<br/>

#### 2-2-3. Variable Scope (!default)

---

<br/>

&nbsp; ์ถ๊ฐ์ ์ธ, `!default` ํ๋๊ทธ๋ฅผ ์ฌ์ฉํ๋ฉด ํด๋น ๋ณ์๊ฐ ์ค์ ๋์ง ์์๊ฑฐ๋ ๊ฐ์ด null๋ ํด๋น ๊ฐ์ ์ฌ์ฉํฉ๋๋ค. (\* ๋๋ถ๋ถ mixin์ ์์ฑ ํ  ๋ ์ฌ์ฉ)

<br/>

```scss
/* Sass */
$personal: #369fff;

$personal: #000 !default;

.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: $personal;
  border-radius: 3px;
  border: 0;
  outline: 0;
}

.p {
  color: $personal;
}
```

<br/>

```css
/* css */
.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: #369fff;
  border-radius: 3px;
  border: 0;
  outline: 0;
}

.p {
  color: #369fff;
}
```

<br/>

### 2-3. Built-in Functions (๋ด์ฅํจ์)

---

<br/>

&nbsp; Sass์์๋ ์ฌ๋ฌ ๋ด์ฅํจ์๋ฅผ ์ ๊ณตํฉ๋๋ค.(`darken`, `lighten`, `saturate` etc...)  
์๋ฅผ๋ค์ด `darken`์ ์๊ณผ ์ธ์๊ฐ์ ๋์ ธ์ฃผ๋ฉด ์ผ๋ง๋ ์ด๋ก๊ฒํ ์ง, `lighten`์ ์ผ๋ง๋ ๋ฐ๊ฒํ ์ง ๊ณ์ฐํ์ฌ์ค๋๋ค.

<br/>

```scss
/* Sass */
$personal: #369fff;

.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: $personal;
  border-radius: 3px;
  border: 0;
  outline: 0;

  &:hover {
    background-color: darken($personal, 10%);
  }
}
```

<br/>

```css
/* css */
.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: #369fff;
  border-radius: 3px;
  border: 0;
  outline: 0;
}

.btn:hover {
  color: #0387ff;
}
```

<br/>

[Sass ๋ด์ฅํจ์ ์์๋ณด๊ธฐ](https://poiemaweb.com/sass-built-in-function)

<br/>

### 2-4. Nesting (์ค์ฒฉ)

---

<br/>

&nbsp; Sass์์๋ ์ ์ธ์ ์ค์ฒฉ์ด ๊ฐ๋ฅํฉ๋๋ค. ๊ธฐ๋ณธ CSS์์๋ ์๋์ ๊ฐ์ด ์์ฑํฉ๋๋ค.

<br/>

```css
/* css */
.wrap {
  width: 100%;
}

.wrap .wrap-title {
  color: #000;
}
```

<br/>

&nbsp; Sass์์๋ ์๋์ ๊ฐ์ด ์์ฑํฉ๋๋ค.

<br/>

```scss
/* Sass */
.wrap {
  width: 100%;

  .wrap-title {
    color: #000;
  }
}
```

<br/>

&nbsp; ๋ ๋ฒํผ์ hover ๊ฒฝ์ฐ๋ฅผ ์์ฑํ์๋ฉด CSS์์๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

```css
/* css */
.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: #369fff;
  border-radius: 3px;
  border: 0;
  outline: 0;
}

.btn:hover {
  color: #0387ff;
}
```

<br/>

&nbsp; Sass์์๋ ๋ถ๋ชจ์ ํ์๋ฅผ ์ฐธ๊ณ ํ ๋ `&`๋ฌธ์๋ฅผ ์ฌ์ฉํ์ฌ ๊ฐํธํ๊ฒ ํํ๊ฐ๋ฅํฉ๋๋ค.

<br/>

```scss
//  Sass
.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: #369fff;
  border-radius: 3px;
  border: 0;
  outline: 0;

  &:hover {
    background-color: darken($personal, 10%);
  }
}
```

<br/>

&nbsp; `@at-root`๋ฅผ ์ฌ์ฉํ๊ฒ๋๋ฉด ์ ํ์ ๋ด๋ถ์ `@at-root ์ ํ์`์ ์ ํ์๋ฅผ ํฌํจํ ๊ฒฝ์ฐ css๋ฅผ ์ ์ฉ์ํต๋๋ค. `.wrap` ๋ด๋ถ์ `@at-root .root`์ ๋ํ css๋ฅผ ์ง์  ํ๊ณ 

<br/>

```scss
// Sass
.wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;

  @at-root .root {
    color: red;
  }
}
```

<br/>

&nbsp; ์๋์ ๊ฐ์ด .wrap ๋ด๋ถ์ .root๋ฅผ ํฌํจํ ์์๊ฐ ์กด์ฌํ๋ค๋ฉด

<br/>

```js
/* Page.jsx */
import React from "react";
import Button from "../components/Button";
import "./Page.scss";

const Page = () => {
  return (
    <div className="wrap">
      <Button />
      <div className="container root">
        container
        <div className="box">box</div>
      </div>
    </div>
  );
};

export default Page;
```

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fuiz7p%2Fbtq1OMe0LLG%2FSOD98aww7liECZ5mD9RJmk%2Fimg.png"/></p>

<br/>

&nbsp; ์์ ๊ฐ์ด ์ ์ฉ์ ๋ฐ๊ฒ ๋ฉ๋๋ค.

<br/>

### 2-5 Import

---

<br/>

&nbsp; `import` ๊ธฐ๋ฅ์ ์ด์ฉํ์ฌ ๋๋ ์ ธ์๋ ์คํ์ผ ํ์ผ๋ค์ ๋ถ๋ฌ์์ ์ฌ์ฉ ํ  ์ ์์ต๋๋ค. ์๋์ ๊ฐ์ ๊ตฌ์กฐ๋ก ์์ ๊ฒฝ์ฐ

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmpZ37%2Fbtq1K3IvwLS%2Fvfkvr53AM3yPnEK2Hxh4K0%2Fimg.png"/></p>

<br/>

&nbsp; \_colors.scss ํ์ผ์ ์์์ ์ฌ์ฉํ  color๋ฅผ ๋ณ์ ์ ์ธ์ ํ๊ณ 

<br/>

```scss
$personal: #369fff;
```

<br/>

&nbsp; ์์ํ  ํ์ผ์์ `@import "path";` ์ ํ์์ผ๋ก ์ ์ธ์ ํ๋ฉด ์๋์ ๊ฐ์ด ์ฌ์ฉ์ด ๊ฐ๋ฅํฉ๋๋ค.

<br/>

```scss
@import "../_common/colors";

.btn {
  padding: 5px 20px;
  color: #fff;
  background-color: $personal;
  border-radius: 3px;
  border: 0;
  outline: 0;

  &:hover {
    background-color: darken($personal, 10%);
  }
}
```

<br/>

> ๐ก Partial ๊ธฐ๋ฅ  
> ๋ง์ฝ .sass ํ์ผ์ด๋ .scss ํ์ผ์ ์ด๋ฆ์ `_`๋ก ์์ ํ  ๊ฒฝ์ฐ css ํ์ผ๋ก ๋ฐ๋ก ์ปดํ์ผ ๋์ง ์์ต๋๋ค.
> ํด๋น css ํ์ผ์ ๋ถ๋ฌ์ฌ ์ผ์ด ์๊ณ  import ๋ง ๋๋๊ฒฝ์ฐ ์ด ๊ธฐ๋ฅ์ ์ฌ์ฉํ์๋ฉด ๋ฉ๋๋ค.

<br/>

### 2-6 Extend

---

<br/>

&nbsp; ํน์  ์ ํ์๋ฅผ ์์ ํ  ๋ `@extend`๋ฅผ ์ฌ์ฉํฉ๋๋ค.

<br/>

```scss
/* Sass */
.box {
  border: 1px solid gray;
  padding: 10px;
  display: inline-block;
}

.success-box {
  @extend .box;
  border: 1px solid green;
}
```

<br/>

```css
/* css */
.box,
.success-box {
  border: 1px solid gray;
  padding: 10px;
  display: inline-block;
}

.success-box {
  border: 1px solid green;
}
```

<br/>

&nbsp; `%`๋ฅผ ์ฌ์ฉํ๋ฉด ์์์ ํ  ์ ์์ง๋ง ํด๋น ์ ํ์๋ ์ปดํ์ผ๋์ง ์์ต๋๋ค.

<br/>

```scss
/* Sass */
%box {
  padding: 0.5em;
}

.success-box {
  @extend %box;
  color: green;
}

.error-box {
  @extend %box;
  color: red;
}
```

<br/>

```css
/* css */
.success-box,
.error-box {
  padding: 0.5em;
}

.success-box {
  color: green;
}

.error-box {
  color: red;
}
```

<br/>

### 2-7 Function

---

<br/>

&nbsp; ์์ Built-in Function๊ณผ๋ ๋ฌ๋ฆฌ ์ฌ์ฉ์ ์ง์  ํจ์์๋๋ค. ํ๋ผ๋ฏธํฐ ๊ฐ์ ๊ณ์ฐํ์ฌ ๊ฐ์ ๋ฐํํ๋ฉฐ `@function`์ ์ฌ์ฉํ์ฌ ์ ์ธํฉ๋๋ค.

<br/>

```scss
// Sass
@function calc-percent($target, $container) {
  @return ($target / $container) * 100%;
}

.my-module {
  width: calc-percent(650px, 1000px);
}
```

<br/>

```css
/* css */
.my-module {
  width: 65%;
}
```

<br/>

### 2-8 Mixin

---

<br/>

&nbsp; Sass์์๋ ๊ฐ์ฅ ์ ์ฉํ ๊ธฐ๋ฅ์ธ Mixin์๋๋ค. `@mixin`์ ์ฌ์ฉํ์ฌ ์ ์ธ์ํ๊ณ  `@include`๋ฅผ ์ด์ฉํ์ฌ ๋ด๋ถ์์ ์ฌ์ฉ์ํฉ๋๋ค.

<br/>

```scss
// Sass
@mixin title {
  font-size: 1.25rem;
  font-weight: 500;
}
@mixin title-sub {
  font-size: 0.875rem;
  font-weight: 400;
}

.title {
  @include title;
}

.title-sub {
  @include title-sub;
}
```

<br/>

```css
/* CSS */
.title {
  font-size: 1.25rem;
  font-weight: 500;
}

.title-sub {
  font-size: 0.875rem;
  font-weight: 400;
}
```

<br/>

## โจ 3. ํ์ฉํ๊ธฐ

<br/>

&nbsp; ํ์ผ ๊ตฌ์กฐ๋ ์๋์ ๊ฐ์ต๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdH7RB2%2Fbtq1KcGiDdG%2FJCUBW1SfoVbNVGpOXwxf00%2Fimg.png"/></p>

<br/>

### 3-1. className ํ์ฉ

<br/>

&nbsp; className์ ์ ๋ฌ๋ฐ์ `size` ๋ฐ๋ผ์ element์ ํฌ๊ธฐ๋ฅผ ๋ณ๊ฒฝํ  ์ ์์ต๋๋ค. "small"๊ณผ "large"์ผ ๊ฒฝ์ฐ์ css๋ฅผ ์์ฑ ํ ๋ค

<br/>

```scss
// Sass
@import "../_common/colors";

.btn {
  color: #fff;
  background-color: $personal;
  border-radius: 3px;
  border: 0;
  outline: 0;

  &.small {
    padding: 5px 20px;
  }

  &.large {
    padding: 10px 40px;
  }

  &:hover {
    background-color: darken($personal, 10%);
  }
}
```

<br/>

```css
/* css */
.btn {
  color: #fff;
  background-color: $personal;
  border-radius: 3px;
  border: 0;
  outline: 0;
}
.btn.small {
  padding: 5px 20px;
}
.btn.large {
  padding: 10px 40px;
}
.btn:hover {
  background-color: #0387ff;
}
```

<br/>

&nbsp; `Button` ์ปดํฌ๋ํธ์ props์ `size`๋ฅผ ๋๊ฒจ์ค๋๋ค.

<br/>

```js
// Page.jsx
import React from "react";
import Button from "../components/Button";
import "./Page.scss";

const Page = () => {
  return (
    <div className="wrap ">
      <Button />
      <Button size="large" />
    </div>
  );
};

export default Page;
```

<br/>

```js
// Button.jsx
import React from "react";
import "./Button.scss";

const Button = ({ size }) => {
  return <button className={`btn ${size}`}>Button</button>;
};

Button.defaultProps = {
  size: "small",
};

export default Button;
```

<br/>

&nbsp; ์ด๋, `size`๋ฅผ ๋๊ฒจ์ฃผ์ง ์์๊ฒฝ์ฐ `Button.defaultProps`์ ์ํด `size`๋ "small"์ด ๋ฉ๋๋ค.

<br/>

<p align="center"><img src="https://blog.kakaocdn.net/dn/byEaGQ/btq1Nu0aHgu/XIkCBbbm6SJgpSeRH1aF4K/img.png"/></p>

<br/>

### 3-2. font-style ํ์ฉ

<br/>

&nbsp; `mixin()`์ ์ฌ์ฉํ์ฌ ๋์์ธ ๊ฐ์ด๋์ ๋ง๋ ํฐํธ ์คํ์ผ์ ๊ด๋ฆฌํ์ฌ ์ฌ์ฉ ํ  ์ ์์ต๋๋ค.

<br/>

```scss
// _font-style.scss
@mixin font-style-24 {
  font-size: 1.5rem;
  font-weight: 500;
  letter-spacing: -0.005em;
}

@mixin font-style-20 {
  font-size: 1.25rem;
  font-weight: 500;
  letter-spacing: -0.05em;
}

@mixin font-style-14 {
  font-size: 0.875rem;
  font-weight: 500;
  letter-spacing: -0.05em;
}

@mixin font($size, $color: false) {
  @if ($size == 24) {
    @include font-style-24;
  }
  @if ($size == 20) {
    @include font-style-20;
  }
  @if ($size == 14) {
    @include font-style-14;
  }

  @if (type-of($color) == color) {
    color: $color;
  }
}
```

<br/>

```js
// Content.jsx
import React from "react";
import "./Content.scss";

const Content = () => {
  return (
    <div>
      <h1 className="title">์ด๊ฒ์ font-style-24 ์๋๋ค.</h1>
      <p className="sub">์ด๊ฒ์ font-style-20 ์๋๋ค.</p>
      <p className="content">์ด๊ฒ์ font-style-14 ์๋๋ค.</p>
    </div>
  );
};

export default Content;
```

<br/>

```scss
@import "../_common/font-style";

.title {
  @include font(24, red);
}

.sub {
  @include font(20, blue);
}

.content {
  @include font(14);
}
```

<br/>

<p align="center"><img src="https://blog.kakaocdn.net/dn/F2BmJ/btq1NtAidFJ/bTpDKT7KD3ZxY62aF57Wpk/img.png"/></p>

<br/>

### 3-3. reponsive ํ์ฉ

<br/>

&nbsp; `mixin()`์ ์ฌ์ฉํ์ฌ Mobile, Tablet, Desktop๋ฑ์ ๊ธฐ๊ธฐ์ ๋์์ด ๊ฐ๋ฅํฉ๋๋ค.

<br/>

```scss
// _media.scss
@mixin media($screen) {
  @if ($screen == T) {
    @media all and (min-width: 768px) and (max-width: 1023px) {
      @content;
    }
  }
  @if ($screen == D) {
    @media all and (min-width: 1024px) {
      @content;
    }
  }
}
```

<br/>

&nbsp; ์ด๋ ํด๋น element์ ์์์ `mixin()`์ ๋ด์ฉ์ ์ ์ํ๊ธฐ ์ํด์๋ `@content`๋ฅผ ์ฌ์ฉํด์ผ ํฉ๋๋ค.

<br/>

```scss
@import "../_common/font-style";
@import "../_common/media";

.title {
  @include font(24, red);
  @include media(T) {
    color: #fff;
    background-color: #000;
  }
  @include media(D) {
    color: #000;
    background-color: #fff;
  }
}

.sub {
  @include font(20, blue);
}

.content {
  @include font(14);
}
```

<br/>

&nbsp; ์ด์ธ์๋ ํ์์ ๋ฐ๋ผ ๋ง์ ์ฉ๋๋ก ํ์ฉ์ด ๋  ์ ์์ต๋๋ค.

<br/>

๐

<br/>

[๋ ์์๋ณด๊ธฐ](https://webclub.tistory.com/category/StyleSheet/SASS%E3%86%8DSCSS)
