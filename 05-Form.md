# Form 

### μμ¬ 1m with Hooks π€ 

#### 1.1 Single Source of truth
**single source of the truth**(μ΄ ν SSOT)μ λν μ μλ₯Ό κ°λ¨ν μ§κ³  λμ΄κ°κ»μ.

> **'μ λ’° κ°λ₯ν λ¨μΌ μΆμ²' 
> νΉμ 
> 'μ μΌν μ€μ μλ£'**

μ΄ν΄νκΈ° μ½κ² νμ΄λ³΄μλ©΄, 
μ μΌλ¬΄μ΄ν λ¨ νλμ κ³΅κΈμ,
μ°λ¦¬μ§μ μλ λ¨ νλμ λμ₯κ³ λΌ,
μ§κΈμ μ΄ν΄νμκΈ°λ₯Ό λ°λμ. 

μμ)
    
    - μ΄μ  λ°λλ μ°μ λ₯Ό 5κ°λ₯Ό κ΅¬λ§€νμ΄μ. 
    - νκ³Ό μ λ§ μλ μ§μ λ¨ νλ μλ λμ₯κ³ μ μ°μ λ₯Ό λ£μ΄λ¨μ΄μ. 
    - μμΉ¨μ μΌμ΄λλ³΄λ 4κ°κ° λ¨μμμ΄μ. (λΆλͺ νμ΄λΌ μμ)
    - νμ μλλμ. 
    - πΆμλ¦¬μμ. 
    - λμ₯κ³ κ° μ°λ¦¬μ§μ λ¨ νλμΈλ° κ·ΈλΌ μ κ° μ΄λ° λκ² μ΄μ?
    - νλ λΏμΈ λμ₯κ³ μμ μμ΄μ§κ±°λ©΄, μμ΄μ§κ±°μμ.
    - λ²μΈμ νλͺ.

β»λ μ νν μκ³  μΆμΌμ  λΆμ΄ κ³μλ€λ©΄ μ΅ νλ¨μ referenceλ₯Ό μ°Έκ³ ν΄μ£ΌμΈμ. 

#### 1.2 Controlled Component(μ μ΄ μ»΄ν¬λνΈ)
react stateλ₯Ό μ°λ¦¬μ§ λμ₯κ³ (SSOT)λ‘ λ§λ€μ΄, 
form elementλ₯Ό μ μ΄λ₯Ό νλ κ²½μ°, 
**Controlled Component**

1. λμ₯κ³ λ₯Ό λ§λ­λλ€!

![image](https://user-images.githubusercontent.com/77006427/112298647-83631500-8cda-11eb-9cfe-ca0fe3c30245.png)

2. μ°λ¦¬ λμ₯κ³ μ λ³΄κ΄ λ μ΄λ¦μ valueλ‘ μ‘μμ€κ±°μμ.

![image](https://user-images.githubusercontent.com/77006427/112298934-9fff4d00-8cda-11eb-83f2-9ee19c71fa76.png)

3. onChange μ΄λ²€νΈκ° λ°μ μ, ν΄λΉ λμ₯κ³ μμ κ΅μ²΄ ν΄μ€κ±°μμ.

![image](https://user-images.githubusercontent.com/77006427/112299072-cae9a100-8cda-11eb-8f1f-186db298fa08.png)

4. νΌμ μ μΆνλ μ΄λ²€νΈκ° λ°μ μ, λμ₯κ³ μ μ§κΈ λ­κ° μλμ§ νμΈ ν  μ μμ΄μ!

![image](https://user-images.githubusercontent.com/77006427/112299440-2451d000-8cdb-11eb-9c74-9ead9711acfb.png)

[Controlled Component μμ μ½λ](https://codesandbox.io/s/controlled-component-epirw?file=/src/ControlledComponent.js)

#### 1.3 Uncontrolled Component(λΉμ μ΄ μ»΄ν¬λνΈ)
react stateκ° μλ DOMμ μ°λ¦¬μ§ λμ₯κ³ (SSOT)λ‘ λ§λ€μ΄, 
form elementλ₯Ό μ μ΄λ₯Ό νλ κ²½μ°, 
**UnControlled Component**


1. λμ₯κ³ κ° μ΄λμ΄μ§ μλ €μ€ μΉκ΅¬λ€μ΄μμ. 

![image](https://user-images.githubusercontent.com/77006427/112300052-cd002f80-8cdb-11eb-8438-e5c43a18d3a3.png)

2. λμ₯κ³ λ μ¬κΈ°μΌ! μλ €μ€λλ€.

![image](https://user-images.githubusercontent.com/77006427/112299882-9aeecd80-8cdb-11eb-99b0-5eadb0f7dde8.png)

3. νΌμ μ μΆ νλ μ΄λ²€νΈκ° λ°μμ, λμ₯κ³ λ μ§κΈ λ­κ° μλμ§ νμΈ ν  μ μμ΄μ.

![image](https://user-images.githubusercontent.com/77006427/112300207-ee611b80-8cdb-11eb-8a85-60755e3ec5c0.png)

![image](https://user-images.githubusercontent.com/77006427/112300570-53b50c80-8cdc-11eb-8129-1de980d7ccce.png)

[Uncontrolled Component μμ μ½λ](https://codesandbox.io/s/controlled-component-epirw?file=/src/UncontrolledComponent.js)

μμ μλ μλ¦¬λ 
jsμμ DOMμ μ‘°μνλ μλ¦¬μ κ°μ λ§₯λ½μ΄λΌκ³  λ³΄μλ©΄ ν¨μ¬ λ μ΄ν΄νκΈ° νΈν©λλ€.

1. form mark-up

![image](https://user-images.githubusercontent.com/77006427/112300735-865f0500-8cdc-11eb-8693-5c733c89d4e5.png)

2. js-form ν΄λμ€λ₯Ό κ°μ§ μΉκ΅¬κ° μ μΆ μ΄λ²€νΈλ₯Ό λ£κ² λλ©΄, 
inputμ΄λΌλ μΉκ΅¬κ° μκΈ°κ° λ­ κ°μ§κ³  μλμ§ μλ €μ€λλ€.

![image](https://user-images.githubusercontent.com/77006427/112300819-9bd42f00-8cdc-11eb-90a9-0395ba1a95b8.png)

[Vanilla JS μμ μ½λ](https://codesandbox.io/s/form-m5k3x)

**reactμμ λ§λ  μνκ° μλ, DOMμ μ§μ  μ κ·Όν΄μ ν΄λΉ elementμ μ λ³΄λ₯Ό κ°μ Έμ¨λ€λΌλ λ§₯λ½μλλ€.**

### μ λ¦¬
λμ₯κ³ λ₯Ό μ΄λμ λ κ²μ΄λμ κΈ°μ€μΌλ‘ μ μ΄/λΉμ μ΄λ‘ λλ μ§λ€κ³  λ³΄λ©΄ λ©λλ€.
**React state** or **DOM**

### β» β  μ£Όμ ν  μ  β 
1. `input type="file"` elementλ λΉμ μ΄ μ»΄ν¬λνΈμλλ€.

2. React κ³΅μλ¬Έμμμλ, controlled componentλ₯Ό λλλ‘ μ¬μ©νλΌκ³  κΆμ₯ν©λλ€.

3. unControlled Componentλ₯Ό λ¬΄μ‘°κ±΄ μ¬μ©νμ§ μλ κ±΄ μλλλ€. λ¨λ°νμ§ λ§λΌλκ²λλ€. :)

   ![image](https://user-images.githubusercontent.com/77006427/112302760-c8894600-8cde-11eb-8d98-fd391f73693b.png) 
  [μΆμ²](https://ko.reactjs.org/docs/refs-and-the-dom.html#when-to-use-refs)

4. κ΅¬ν νκ³  μΆμ κΈ°λ₯μ λ°λΌ, μ νν΄μ μ¬μ©νλ©΄ λ©λλ€.

![image](https://user-images.githubusercontent.com/77006427/112302222-2f5a2f80-8cde-11eb-9800-10a79165691e.png)

References:
- [Single Source of Truth](https://en.wikipedia.org/wiki/Single_source_of_truth)
- [μλ μμ΄λ μΉ νν - νΌμ λν μ μ](https://www.w3.org/TR/html401/interact/forms.html)
- [νΌ μ°λκΈ°](https://www.ventureharbour.com/the-evolution-of-web-forms/#:~:text=The%20first%20generation%20of%20true,of%20Web%202.0%20in%202004)
- [νΌ κ³΅μλ¬Έμ](https://reactjs.org/docs/forms.html)
- [λΉμ μ΄ μ»΄ν¬λνΈ](https://reactjs.org/docs/uncontrolled-components.**html**)
- [useRef](https://reactjs.org/docs/hooks-reference.html#useref)
