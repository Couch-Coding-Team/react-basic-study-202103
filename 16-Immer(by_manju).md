# Immer

๐ค **Why is Immutability important in React??**

- React๋ state๊ฐ ๋ณํ  ๋ ๊ทธ๊ฑธ `์ธ์ง`ํ๊ณ  re-renderingํฉ๋๋ค. ๊ทธ๋ผ React๋ ์ด๋ป๊ฒ ์ด `๋ณํ๋ฅผ ์ธ์ง`ํ๋ ๊ฑธ ๊น์? 

- ์ด๋ค๊ฒ ๋ณํ๋ค๋ ์ฌ์ค์ ์๊ธฐ ์ํด์๋ ์ผ๋จ ๋น๊ต ๋์, ์ฆ ์๋ณธ์ด ์์ด์ผ '์! ์๋ณธ์ด ๋ณํ๊ตฌ๋'๋ผ๋ ๊ฑธ ์ ์ ์์ต๋๋ค. ๊ทธ๋ฌ๋ฏ๋ก **์๋ณธ์ ๋ณต์ฌํด์ ๊ทธ ๋ณต์ฌ๋ณธ์ ์์ ํ ๋ค์ ์๋ณธ๊ณผ ๋ณต์ฌ๋ณธ์ ๋น๊ตํ๋ฉด `"์๋ณธ์ด ๋ณํ๋ค"`๋ ์ฌ์ค๊ณผ "์ด๋ค ๋ถ๋ถ์ด ๋ณํ๋ค"๋ฅผ ์ ์ ์์ต๋๋ค.**

- ํ์ง๋ง ๊ฐ์ฒด์ ํ๋กํผํฐ๋ฅผ ํ๋ ํ๋ ๋น๊ตํ๋ฉด์ ์ด๋ค๋ถ๋ถ์ด ๋ณํ์ง๋ฅผ ๋จผ์  ์ฐพ๊ณ  ๋ณํ ์ฌ์ค์ ์ธ์งํ๋ ๊ฑด ๊ฐ์ฒด๊ฐ ๊น์ด ์ง์๋ก ์๊ฐ์ด ์ค๋ ๊ฑธ๋ฆฌ๊ณ  ๊ณผ์ ์ด ๋ณต์กํด์ง๋๋ค. 

    ```jsx
    const userState = {
        name: 'Choi', 
        age: '25', 
        loginToken: 'asfwerasdf', 
        friends: ['Lee', 'Park'], 
        skills: { 
            frontEnd: ['React', 'Vue', 'jQuery', 'HTML','CSS'], 
            backEnd: ['Node.js'], 
            common: ['TS'] 
            } 
        }
    ```

    ์๋ฅผ ๋ค์ด, ์์ ๊ฐ์ ๊ฐ์ฒด๊ฐ ์์ ๋ 'skills' ๊ฐ์ฒด ํ๋กํผํฐ์์, 'backend' ํ๋กํผํฐ์ 'JAVA'๋ฅผ ์ถ๊ฐํ๋ค๋ฉด React๋ ๋ณํํ๋ค๋ ๊ฑธ ์์๋ด๊ธฐ ์ํด ๋ชจ๋  ํ๋กํผํฐ๋ฅผ ํ๋ํ๋ ๋น๊ตํด์ผ ํฉ๋๋ค. 

- ๊ทธ๋์ React๋ `์๋ณธ์ด ๋ณํ๋ค`๋ ์ฌ์ค๋ง ๋น ๋ฅด๊ฒ ์์๋ด๊ณ  re-rendering์ ํฉ๋๋ค. ์ด๋ ๊ฒ `์๋ณธ์ด ๋ณํ๋ค๋ ์ฌ์ค`์ ์ ์ผ ๋นจ๋ฆฌ ์์๋ผ ์ ์๋ ๋ฐฉ๋ฒ์ด ์ฐธ์กฐ ๊ฐ์ด ๋ค๋ฅธ ๋ณต์ฌ๋ณธ์ ๋ง๋๋ ๊ฒ์๋๋ค. ๊ฐ์ฒด ๋ด๋ถ๋ฅผ ๊น์ด ๋ค์ฌ๋ค ๋ณผ ํ์ ์์ด, ์์ ๊ฐ์ฒด ์์ฒด๊ฐ ๋ค๋ฅธ ์ฐธ์กฐ๊ฐ์ ๊ฐ์ง๋ ๋ณต์ฌ๋ณธ์ ๋ง๋ค์ด ๋๋ค๋ ๊ฒ์ ๊ทธ ๊ฐ์ฒด๋ฅผ ๋ณํ๊ฒ ํ ๊ฑฐ๋ผ๋ ์๋ฏธ์ ๋์ผํ๋ฏ๋ก re-rendering์ ๊ฒฐ์  ํฉ๋๋ค. 

<br>

## Make copy using Javascript

- array.concat()

    ```jsx
    handleClick() {
    this.setState(state => ({
        words: state.words.concat(['marklar'])
    }));
    }
    ```

- spread syntax

    ```jsx
    handleClick() {
    this.setState(state => ({
        words: [...state.words, 'marklar'],
    }));
    };
    ```

- Object.assign()

    ```jsx
    function updateColorMap(colormap) {
        return Object.assign({}, colormap, {right: 'blue'});
    }
    ```

>๊ฐ๋จํ๊ฒ ์์ ํจ์ ์ฐ์ตํด๋ณด๊ธฐ: <https://codesandbox.io/s/suspicious-resonance-lv6wj>

<br>

๐ค **Why we need 'Immer'?**

- ์์์ ์ดํด๋ดค๋ฏ์ด, ๋ถ๋ณ์ฑ์ ์ ์งํ๊ธฐ ์ํด javascript์์ ์๋ ๋ถํฐ ์ฌ์ฉ๊ฐ๋ฅํ ํจ์๋ค์ด ์์ต๋๋ค. ๊ทธ๋ผ ์ด๋จ ๋ 'Immer' library๋ฅผ ์ฌ์ฉํ๋ฉด ์ข์๊น์??

    ```jsx
    const user = { 
        name: 'Choi', 
        age: 25, 
        friends: ['Park', 'Kim']
        } 

    const otherUser = { ...user }; 

    user.name = 'Lee'; 

    user.friends.push('Kang'); 

    /* user = { name: 'Lee', age: 25, friends: ['Park', 'Kim', 'Kang'] } 
    otherUser = { name: 'Choi', age: 25, friends: ['Park', 'Kim', 'Kang'] } */ 

    user === otherUser // false 
    user.friends === otherUser.friends // true
    ```

    spread syntax๋ก otherUser๋ผ๋ ๋ณต์ฌ๋ณธ ๊ฐ์ฒด๋ฅผ ๋ง๋ค์์ต๋๋ค. user.name์ ๋ฐ๊ฟ์ค ๊ฒ์ otherUser์ ๋ฐ์๋์ง ์์์ง๋ง user.friends.push()๋ฅผ ํ์ ๋ ๋ ๊ฐ์ฒด๊ฐ ๊ฐ์ด ๋ฐ๋๋๋ค. React๋ผ๊ณ  ์๊ฐ ํ์ ๋ ์ด๋ค ๋ฌธ์ ๊ฐ ์๊ธธ๊น์?

<br>

- ์์ ๊ฐ์ด ์ฐ๋ฆฌ๊ฐ ์์ฃผ ์ฌ์ฉํ๋ spread syntax๋  shallow copy(์์ ๋ณต์ฌ)๋ฅผ ํ๊ฒ ๋๋๋ฐ, ์ ํฌ๊ฐ ์ํ๋ ๊ฑด ์์ ํ ๋ค๋ฅธ ๊ฐ์ฒด๋ฅผ ๋ง๋ค๋, ์์ ๋ด์ฉ์ ์์ ํ ๋๊ฐ๊ธฐ๋ฅผ ์ํฉ๋๋ค. ์ด๊ฑธ ๋ฐ๋ก deep copy(๊น์ ๋ณต์ฌ)๋ผ๊ณ  ํ๋ ๋ฐ, ๊ฐ์ฒด๊ฐ ๊น์ด์ง ์๋ก deep copy๋ ์ด๋ ค์์ง๋๋ค. ์ด ๋ ์ฌ์ฉ ๊ฐ๋ฅํ ๊ฒ์ด ๋ฐ๋ก **'Immer' library** ์๋๋ค. 

<br>

## How Immer works

- ์ด๋ค ๊ฐ์ฒด๊ฐ ์๋ค๊ณ  ํ์ ๋, immer์ ์์ฒด์ ์ผ๋ก ๊ทธ ๊ฐ์ฒด์ drafState๋ฅผ ๋ง๋ญ๋๋ค. ์ด ๋ณต์ฌ๋ณธ์์ ์ํ๋ ๋๋ก ์์ ์ ๋๋ด๋ฉด immer๋ ๊ทธ ์์ ๋ ์ฌํญ๋ค์ ๋ฐ์ํ nextState๋ฅผ ๋ง๋ญ๋๋ค. 


    ![image](https://user-images.githubusercontent.com/75834421/113087067-d4fd2980-921d-11eb-811a-9072c9ed7d6b.png)

<br>

- immer ์ ์ฌ์ฉํ๊ธฐ ์ํด์  ์ธ๋ถ library์ด๋ฏ๋ก ์ค์น๊ฐ ํ์ํฉ๋๋ค.

    ```jsx
    $ npm install immer 
    ```

- ๊ทธ๋ฆฌ๊ณ  ์์ฑ์ค์ธ ์ฝ๋ ์๋จ์์ import ํด์ฃผ์ด์ผ ํฉ๋๋ค.

    ```jsx
    import produce from 'immer';
    ```

- produce ํจ์๋ฅผ ์ฌ์ฉ ํ  ๋์๋ ์ฒซ๋ฒ์งธ ํ๋ผ๋ฏธํฐ์๋ **์์ ํ๊ณ  ์ถ์ ์ํ**, ๋๋ฒ์งธ ํ๋ผ๋ฏธํฐ์๋ **์ด๋ป๊ฒ ์๋ฐ์ดํธํ๊ณ  ์ถ์์ง ์ ์ํ๋ ํจ์**๋ฅผ ๋ฃ์ด์ค๋๋ค.

    ```jsx
    //immer์ฌ์ฉ ์  
    case "CREATE_USER":
        return {
            inputs: initialState.inputs,
            users: state.users.concat(action.user)
        }
    case "REMOVE_USER":
        return {
            ...state,
            users: state.users.filter(user => user.id !== action.id)
        }
    case "TOGGLE_USER":
        return {
            ...state, 
            users: state.users.map(user => 
                user.id === action.id ? {...user, active: !user.active} : user
            )
        };

    //immer ์ฌ์ฉ ํ
    case 'CREATE_USER':
        return produce(state, draft => {
            draft.users.push(action.user);
        });
    case 'REMOVE_USER':
        return produce(state, draft => {
            const index = draft.users.findIndex(user => user.id === action.id);
            draft.users.splice(index, 1);
        });
    case 'TOGGLE_USER':
        return produce(state, draft => {
            const user = draft.users.find(user => user.id === action.id);
            user.active = !user.active;
        });
    ```

    >๐ ์ฌ๊ธฐ์ ์ ์ ์๋ฏ์ด ๊ฐ์ฒด๊ฐ ๊น์ง ์๊ฑฐ๋, immutability๋ฅผ ์ ์งํ๊ธฐ์ํด ์ฝ๋๊ฐ ๊ธธ์ด ์ง๋ ๊ฒฝ์ฐ๊ฐ ์๋ ์ด์ immer์ ์ฌ์ฉํ์ง ์์๋ ๋ฉ๋๋ค. ์ต๋ํ ์ผ๋ฐ javascript๋ก ๊ตฌํํ๊ณ , ํ์ํ ๊ณณ์๋ง immer์ ์ฌ์ฉํฉ๋๋ค! 

<br>

- React์ setState์ ๊ฐ์ด ์ฌ์ฉํ๊ธฐ 

    : ์ฒซ๋ฒ์งธ ํ๋ผ๋ฏธํฐ๋ฅผ ์๋ตํ๊ณ  ๋ฐ๋ก ์๋ฐ์ดํธ ํจ์๋ฅผ ๋ฃ์ด์ฃผ๊ฒ ๋๋ค๋ฉด, ๋ฐํ ๊ฐ์ ์๋ก์ด ์ํ๊ฐ ์๋ `์ํ๋ฅผ ์๋ฐ์ดํธ ํด์ฃผ๋ ํจ์`๊ฐ ๋ฉ๋๋ค.

    ```jsx
    const todo = {
    text: 'Hello',
    done: false
    };

    const updater = produce(draft => {
    draft.done = !draft.done;
    });

    const nextTodo = updater(todo);

    console.log(nextTodo);
    // { text: 'Hello', done: true }
    ```
    <br>

    : setTodo ํจ์์์ ํจ์ํ ์๋ฐ์ด๋ฅผ ํจ์ผ๋ก์จ, useCallback ์ ์ฌ์ฉํ๋ ๊ฒฝ์ฐ ๋๋ฒ์งธ ํ๋ผ๋ฏธํฐ์ธ deps ๋ฐฐ์ด์ todo ๋ฅผ ๋ฃ์ง ์์๋ ๋ฉ๋๋ค. ์ด๋ ๊ฒ setState(์ฌ๊ธฐ์๋ setTode)๋ ํจ์๋ฅผ ๊ฐ์ง ์ ์์ผ๋ฏ๋ก ์์ ๊ฐ์ ์ฒซ๋ฒ์งธ ํ๋ผ๋ฏธํฐ๋ฅผ ์๋ตํ produceํจ์๋ฅผ ๊ฐ์ง ์ ์์ต๋๋ค. 

    :produce ๊ฐ ๋ฐํํ๋๊ฒ์ด ์๋ฐ์ดํธ ํจ์๊ฐ ๋๊ธฐ ๋๋ฌธ์ useState ์ ์๋ฐ์ดํธ ํจ์๋ฅผ ์ฌ์ฉ ํ  ๋ ๋ค์๊ณผ ๊ฐ์ด ๊ตฌํ ํ  ์ ์๊ฒ ๋ฉ๋๋ค.

    ```jsx
    //immer ์ฌ์ฉ ์ 

    const [todo, setTodo] = useState({
        text: 'Hello',
        done: false
    });

    const onClick = useCallback(() => {
        setTodo(todo => ({
            ...todo,
            done: !todo.done
        }));
    }, []);

    //immer์ฌ์ฉ ํ 
    const [todo, setTodo] = useState({
        text: 'Hello',
        done: false
    });

    const onClick = useCallback(() => {
    setTodo(
        produce(draft => {
        draft.done = !draft.done;
        })
    );
    }, []);
    ```

    <br>

์ฐธ๊ณ ์๋ฃ
- Immutability in React with Immer: <https://blog.logrocket.com/immutability-in-react-with-immer/>

- Pros and Cons of using immutability with React.js: <https://reactkungfu.com/2015/08/pros-and-cons-of-using-immutability-with-react-js/>

- React์์ ๋ถ๋ณ์ฑ์ ์ง์ผ์ผ ํ๋ ์ด์ : <https://webigotr.tistory.com/293>

- immer ๊ณต์ ํ์ด์ง: <https://immerjs.github.io/immer/>
