# CUSTOM HOOKs ์์ฌ 50cm ๐

## TELEPATHY
---
**๋์ผํ ์ปดํฌ๋ํธ ๋ก์ง**์ด, **๋ณต์์ ์ปดํฌ๋ํธ**์ ์ค๋ณต ์ฌ์ฉ ๋๋ค๋ฉด,  
 
 ![image](https://user-images.githubusercontent.com/77006427/113147643-ec630380-926b-11eb-8675-a1247817c40b.png)

`Custom Hook`๋ฅผ ๋ง๋ค๋ผ๋ ์ ํธ์๋๋ค.


๋์ฒด ๋ฌด์จ ์ผํ ๋นํ  ์๋๋ ๋ง๋ฅผ ํ๊ณ  ์๋ ๊ฒ์ธ์ง  
์ค๋นํ ์ฝ๋๋ฅผ ์ดํด๋ณด๋ฉฐ  
ํ์ธํด๋ณด๊ฒ ์ต๋๋ค.

---

๊ฐ๋จํ Form ์ฝ๋์๋๋ค. 
(*Controlled Component* ๊ธฐ์ต๋์๋์...?)


```bash
function Form() {
  const [isValid, setValid] = useState(fals
  return (
    <div className="Form">
      <label htmlFor="password">Password: </label>
      <input
        id="password"
        onChange={e => {
          const newValue = e.target.value;
          let _isValid = false;
          if (newValue.length >= 8) _isValid = true;
          setValid(_isValid);
        }}
      />
      {isValid ? <p>Your password is valid </p> : null}
    </div>
  );
}
```

์์ ์ฝ๋๋ ๋ค์๊ณผ ๊ฐ์ต๋๋ค. 

1. password๋ฅผ ์๋ ฅํ๋ input
2. password์ ๊ฐ์ด ๋ณ๊ฒฝ์ด ๋  ์์, ํด๋น password์ ๊ฐ์ ๊ฒ์ฆํด์ฃผ๋ onChange ํจ์
3. ๊ฒ์ฆ์ ํฉ๋นํ  ์, ์๋ ฅ๋ password๋ ๊ฒ์ฆ๋ฌ๋ค๋ ๋ฉ์ธ์ง๋ฅผ ์ฌ์ฉ์์๊ฒ ๋ณด์ฌ์ค๋ค. 

โป ์์ 2๋ฒ์ ๋ก์ง์์๋ ๊ธธ์ด๊ฐ 8๊ฐ ์ด์์ธ ๊ฒฝ์ฐ, validation์ ํต๊ณผํฉ๋๋ค.

---

์ด์  ์์ ๊ฐ์ด validation ๋ก์ง์ ์ ์ฉํด์ผ๋๋ Form์ด 
๊ตฌ์ถํ๊ณ  ์๋ ์ฌ์ดํธ์์ 20๊ตฐ๋ฐ๋ ์๋ค๊ณ  ๊ฐ์ ํด๋ด์๋ค.

์ผ์ผ์ด onChange์ ๋์ผํ validation ๋ก์ง์ ๊ธฐ์ํ๊ฒ ๋ค ๋ค์งํ์์ผ๋ฉด,  
๊ฐ๋ฐ์ด ๊ณผ์ฐ ์๊ธฐ์ ์ง๋ก์ธ๊ฐ์ ๋ํด ๊น๊ฒ ๊ณ ๋ คํด๋ณด์์ผ๋ฉ๋๋ค. 

๊ฐ์คํ๊ณ ,  

์์ ๊ฐ์ด ์ค๋ณต๋๋ ๋ก์ง์ด ๋ณด์ด๋ฉด **๋ถ๋ฆฌ๋ฅผ ์์ผ์ค์ผ ๋ ๊ฑฐ๊ฐ์๋ฐ?** ๋ผ๋ `์ ํธ`๋ก ๋ณด์๋ฉด ๋ฉ๋๋ค.


Valiadtion ๋ก์ง์ด ๋ถ๋ฆฌ๋ ์ฝ๋๋ฅผ ์ดํด๋ณด๊ฒ ์ต๋๋ค.
```bash
function Form() {
  const [isValid,onPasswordChange] = useSmartPassword();
  return (
    <div className="Form">
      <label htmlFor="password">Password: </label>
      <input
        id="password"
        onChange={e => onPasswordChange(e)}
      />
      {isValid ? <p>Your password is valid </p> : null}
    </div>
  );
}

function useSmartPassword(){
  const [isValid, setValid] = useState(false);

  const onChange= e => {
    const newValue = e.target.value;
    let _isValid = false;
    if (newValue.length >= 8) _isValid = true;
    setValid(_isValid);
  };

  return [isValid, onChange]; 
}
```
[์๋๋ฐ์ค ๋งํฌ](https://codesandbox.io/s/react-custom-hooks-1zlvc?file=/src/index.js)

1. **useSmarPassword**๋ผ๋ custom hook function์ ๋ง๋ ๋ค.   
(use ์ ๋์ด๋ custom hook์ rules of hook์ ์ ์ฉํ๊ธฐ ์ํด ๋ถ์ฌ์ผ๋ฉ๋๋ค.)
1. custom hook์ useState๋ฅผ ์ฌ์ฉํจ์ผ๋ก stateful ํ๊ฒ ๋ง๋ ๋ค.
`const isValid, setValid] = useState(false)` 
3. ์ด์ ์ ์ค๋ชํ์๋ ๋ก์ง์ด ํฌํจ๋ ํจ์๋ฅผ ์ ์ธํ๋ค. (`onChange`)
4. ํด๋น ๋ก์ง์ ์ธ๋ถ์์ state๋ฅผ ๋ฐ์์ custom hook์์ ์ํ๋ฅผ ์๋ฐ์ดํธ์์ผ์ค๋ค.
`onChange={(event) => onPasswordChange(event)}`
5. ํด๋น custom hook์ ์ํ์ ๋ก์ง์ ๊บผ๋ด Form์์ ์ฌ์ฉํ๋ค. `[isValid, on PasswordChange] = useSmartPassword()`

### ์ ๋ง ๊ฐ๋จํ์ง ์๋์? ๐


๊ฐ์ฒด์์๋ง destructing ํ๋๊ฒ ์๋ ๋ฐฐ์ด์์๋ ๊ฐ๋ฅํ๋ค๋ ์  ์ ์ํ์๋ฉด ๋๊ฒ ์ต๋๋ค.

ํด๋น ์์์์๋ ๋ฐฐ์ด์ ๋ฐํํ์ง๋ง,   
๊ผญ ๋ฐฐ์ด์ด ์๋๋๋ผ๋ ์ํ๋ ๋ก์ง์ ๋ฐํํ์ฌ ์ด๋์๋  ์ฌ์ฉ ๊ฐ๋ฅํฉ๋๋ค. 

---

### โ  ์ฃผ์ โ 

Custom Hook์ ์ฌ์ฉํ๋ฉฐ ์ฃผ์ํ์์ผ ๋  ์ ์,  
๊ธฐ์กด์ Hook์ ์ฌ์ฉํ๋ ๋ฐฉ๋ฒ๊ณผ ๋์ผํฉ๋๋ค.  

- ๋ฆฌ์กํธ ์ปดํฌ๋ํธ์์ ์ฌ์ฉํ  ๊ฒ (TOP LEVEL์์)
- ์ปค์คํ ํ์์ ์ฌ์ฉ ํ  ๊ฒ,  


custom hook within custom hook with custom hook  
![image](https://user-images.githubusercontent.com/77006427/113161835-b593ea00-9279-11eb-9a70-1b299707a9a2.png)

์ด๋ฏธ ๋ง๋ค์ด์ ธ์๋ ์ข์ custom hook๋ค์ด ๋ง์ต๋๋ค. ์ฐพ์๋ณด๊ณ  ์์ผ๋ฉด ๋ง๋ค์ด๋ด์๋ค.  
[๊นํ ๋งํฌ](https://github.com/rehooks/awesome-react-hooks)


### ์ฌ๋ด
---
์ธํฐ๋ท์ ๋๋ฆฌ๊ณ  ๋๋ ค์๋ ์์๋ค์ ์ดํด๋ณด๋ฉด,   
> ์ค๋ณต๋๋ ๋ก์ง์ ๋ฆฌํฉํ ๋งํด์, ์ด๋์๋ ์ฌ์ฉ ๊ฐ๋ฅํ๊ฒ ๋ง๋ค ์ ์๋๊ฒ ๋ฐ๋ก ์ปค์คํํ์ด์ผ
์ฉ์ง? ๐ฉโ๐ป


์ ๋ง ์ข์ต๋๋ค. ใใ


๊ทผ๋ฐ ์ด ์ ํธ์ ๋ํด ๋ค๋ฅด๊ฒ ํด์ํด๋ณด์๋ฉด...

๋ฐ๋ก๐ 

>Whenever you see a component knowing more than it should,
>it should a sign that you might need to refactor it.

ํ๋์ ์ปดํฌ๋ํธ์ ์ฌ๋ฌ ๊ด์ฌ์ฌ๊ฐ ์ง์ค ๋์์ ๊ฒฝ์ฐ,  
๋ก์ง์ ๋ฐ๋ก ๋ถ๋ฆฌํด์ ๊ด๋ฆฌํ๋๊ฒ ์ข๋ค๋ผ๋ ๊ด์ ๋ ์๋ค๊ณ  ๋ณด์ฌ์ง๋๋ค.

๊ด์ฌ์ฌ์ ๋ถ๋ฆฌ๋ผ๋ ๊ฐ๋์๋๋ค... 
๊ถ๊ธํ์  ๋ถ๋ค์ ๊ตฌ๊ธ์ separation of concerns ์ ๊ฒ์ํด๋ณด์๊ธฐ๋ฅผ ์ถ์ฒ๋๋ฆฝ๋๋ค.
๋น๋จ, ๋ฆฌ์กํธ์์๋ง ๋ค๋ฃจ๋ ๊ฐ๋์ด ์๋, ํ๋ก๊ทธ๋๋ฐ์ ์ด๋ป๊ฒ ์์ฑ ํ  ๊ฒ์ธ์ง ๋ํ ํฐ ๊ฐ๋์ด๊ธฐ์,  
ํ๋ฒ ์ดํด๋ณด์๋ ๊ฒ์ ๊ฐ๋ ฅ์ถ์ฒ๋๋ฆฝ๋๋ค. 

์ ๋ฆฌํ์  ๊ธ ๊ณต์  ๊ธฐ๋ค๋ฆฌ๊ฒ ์ต๋๋ค.  
![image](https://user-images.githubusercontent.com/77006427/113154325-e290ce80-9272-11eb-8a48-bd5542462419.png)



References: 
- [BYOH](https://reactjs.org/docs/hooks-custom.html)
- [Rules of Hooks](https://reactjs.org/docs/hooks-rules.html)
- [Your First Custom Hook](https://itnext.io/react-custom-hooks-basics-f92de2a0ac0e)






