# Context in React

## ๐ค Why we use Context?

<br>

![image](https://user-images.githubusercontent.com/75834421/113876415-b2a57600-97f2-11eb-9ad2-c58671115b0a.png)

React๋ ์๋๋ถํฐ component๋ก ์๊ฒ ์ชผ๊ฐ์ ํ๋์ ํฐ ์ดํ๋ฆฌ์ผ์ด์์ ์ ๋ง๋ค ์ ์๋ Library(ํน์ Framwork..?) ์๋๋ค. ์์ ๊ทธ๋ฆผ ์ฒ๋ผ, ๊ฐ๊ฐ์ component์ ๊ณตํต์ ์ธ state๊ฐ ํ์ํ  ๋ ๋ชจ๋  components๋ฅผ ํฌํจํ๋ ์์ฃผ ํฐ! super big component์ผ๋ก ์ธ์ ๊ด๋ฆฌํ๋ฉด ๋ฉ๋๋ค!

<br>

![image](https://user-images.githubusercontent.com/75834421/113877433-aa9a0600-97f3-11eb-895d-3aea71fb588c.png)

๊ทธ๋ผ ์ด๋ ๊ฒ ๊น๊ฒ component๊ฐ ๊ตฌ์ฑ๋์ด ์์ ๋ ์ด๋ป๊ฒ ํด์ผ ํ ๊น์?๋ณดํต ๋ถ๋ชจ component์์ ์ ์ํ state๋ฅผ ์์ component์์๋ ์ฌ์ฉํ๊ธฐ ์ํด์  props๋ก ์ ๋ฌํด ์ฃผ์ด์ผํฉ๋๋ค. big component(ํ๋์) ์์ ์ ์ํ ์ํ๋ฅผ ์ฃผํฉ์ ๋๊ทธ๋ผ๋ฏธ์์ ์ฐ๋ ค๋ฉด ๋๋ฌด๋ ๋ง์, props ์ ๋ฌ ๋ง์ ์ํ component๋ค์ด ํ์ํด์ง๋๋ค!! ์ฌ๊ธฐ์ ํ์ํ๊ฒ ๋ฐ๋ก **Context**์๋๋ค.

<br>

![image](https://user-images.githubusercontent.com/75834421/113878246-652a0880-97f4-11eb-952f-b90aa413528a.png)

๊ฐ component์ ํ์ํ state(data) ๋ค์ ํ ๊ณณ์ ๋ชจ์๋๊ณ , ํ์ํ  ๋๋ง๋ค ๋ถ๋ฌ์ค๊ณ , ์ฌ์ฉํ๋ component์์์ ์๋ก์ด ์ํ๋ก ๋์ฒดํ  ์ ์์ต๋๋ค. ์ด๋ ๊ฒ React์์ **state managemen๋ฅผ ๊ฐ๋ฅํ๊ฒ ํด์ฃผ๋ ๊ฒ์ด
`Context`**๋ผ๊ณ  ํ ์ ์์ต๋๋ค.

<br>

<br>

## ๐ค How to use Context

<br>

> **Context์ ์์ฃผ ๊ฐ์ด ์ฐ์ด๋ useReducer!**
>
> ๊ฐ์ฅ ๋ง์ด ์ฐ์ด๊ณ  ์ ๋ชํ useState๋์ ์ useReducer์ ์ด๋ค๋ ๊ฑด ๊ทธ๋งํผ ๊ด๋ฆฌํด์ผํ๊ณ  ์ฌ์ฉํ๋ state๊ฐ ๋ง๋ค๋ ์๋ฏธ์๋๋ค. ์ฆ, ๋ง์ state๋ฅผ ํ ๊ณณ์์ ํธํ๊ฒ ๊ด๋ฆฌ ํ  ์ ์๋ Context์ ๊ฐ์ด ์ฐ๋ฉด ๋งค์ฐ ํธ๋ฆฌํฉ๋๋ค!!
>
> - `reducer` function : reducer function์์ ๋ฐํ๋๋ object๊ฐ ์๋ก์ด state๋ก์์ object๋ก **๋์ฑ**๋ฉ๋๋ค.
>
> - `dispatch` : reducer function์ด state์ action์ ๊ฐ์ง๊ณ  ๋ค์(์๋กญ๊ฒ) ์คํํ๊ฒ ๋ ๋ง๋ค์ด ์ค๋๋ค! (=> ์ด๋ก ์ธํด ์คํ๋๋ reducerํจ์์ return ๊ฐ์ด state๋ก ๋์ฑ๋๋ ๊ฒ!!)
>
> <br>

<br>

<br>

### ๐ Example(To do List)

<br>

- Context๋ฅผ ์์ฑํ๋ component

  ```jsx
  import React, { createContext, useReducer, useContext } from "react";
  import reducer, { initialState } from "./reducer";

  // todolist๋ฅผ ๋ง๋ค๊ธฐ ์ํ data box = context ๋ง๋ค๊ธฐ
  const ToDosContext = createContext();

  const ToDosProvider = ({ children }) => {
    // dispatch์ reducer๋ก state๋ฅผ ๊ด๋ฆฌํ  useReducer
    const [state, dispatch] = useReducer(reducer, initialState);
    return (
      <ToDosContext.Provider value={{ state, dispatch }}>
        {children}
      </ToDosContext.Provider>
    );
  };

  // useDispatch์ useState๋ฅผ ์ฌ์ฉํด์ ๋ค๋ฅธ component์์
  // TodoContext์ ์๋ state๋ dispatch๋ฅผ ์ฌ์ฉํ๊ธฐ
  export const useDispatch = () => {
    const { dispatch } = useContext(ToDosContext);
    return dispatch;
  };

  export const useState = () => {
    const { state } = useContext(ToDosContext);
    return state;
  };

  export default ToDosProvider;
  ```

<br>

- ์๋ก์ด ์ํ๋ฅผ ๋ฐํํด์ค reducer function

  ```jsx
  import uuid from "uuid/v4";
  import { ADD, COMPLETE, DEL, UNCOMPLETE } from "./actions";

  export const initialState = {
    toDos: [],
    completed: [],
  };

  const reducer = (state, action) => {
    switch (action.type) {
      case ADD:
        return {
          ...state,
          toDos: [...state.toDos, { text: action.payload, id: uuid() }],
        };
      case DEL:
        return {
          ...state,
          toDos: state.toDos.filter((toDo) => toDo.id !== action.payload),
        };
      case COMPLETE:
        const target = state.toDos.find((toDo) => toDo.id === action.payload);
        return {
          ...state,
          toDos: state.toDos.filter((toDo) => toDo.id !== action.payload),
          completed: [...state.completed, { ...target }],
        };
      case UNCOMPLETE:
        const aTarget = state.completed.find(
          (toDo) => toDo.id === action.payload
        );
        return {
          ...state,
          completed: state.completed.filter(
            (toDo) => toDo.id !== action.payload
          ),
          toDos: [...state.toDos, { ...aTarget }],
        };

      default:
        return;
    }
  };
  ```

<br>

- Context์์ state๋ฅผ ๊ฐ์ ธ๋ค ์ฐ๋ App.js

  ```jsx
  import React from "react";
  import { useState } from "../context";
  import Add from "./Add";
  import List from "./List";
  import ToDo from "./ToDo";

  //useState๋ก toDos์ completed๋ฅผ ์ ์ํจ์ผ๋ก์
  //context(data box)์์ ์ ์๋์ด ์๋ state = { toDos, completed} ๋ฅผ ์ฌ์ฉํ  ์ ์์!
  function App() {
    const { toDos, completed } = useState();
    return (
      <>
        <Add />
        <List name={"To Do"}>
          {toDos.map((toDo) => (
            <ToDo key={toDo.id} id={toDo.id} text={toDo.text} />
          ))}
        </List>

        <List name={completed.length !== 0 ? "Completed" : ""}>
          {completed.map((toDo) => (
            <ToDo
              key={toDo.id}
              id={toDo.id}
              text={toDo.text}
              isCompleted={true}
            />
          ))}
        </List>
      </>
    );
  }

  export default App;
  ```

    <br>

- Context์์ dispatch๋ฅผ ๊ฐ์ ธ๋ค ์ฐ๋ ToDo.js

  ```jsx
  import { COMPLETE, DEL, UNCOMPLETE } from "../actions";
  import { useDispatch } from "../context";

  const ToDo = ({ text, id, isCompleted }) => {
    const dispatch = useDispatch();
    return (
      <li>
        <span>{text}</span>
        <span
          role="img"
          aria-label=""
          onClick={() => dispatch({ type: DEL, payload: id })}
        >
          โ
        </span>
        <span
          role="img"
          aria-label=""
          onClick={() =>
            dispatch({ type: isCompleted ? UNCOMPLETE : COMPLETE, payload: id })
          }
        >
          {isCompleted ? " ๐๐ผโโ๏ธ" : "โ"}
        </span>
      </li>
    );
  };

  export default ToDo;
  ```

<br>

- Provider๋ก App component ๊ฐ์ธ์ฃผ๊ธฐ! (`์ด App component์์ ๋ด๊ฐ ์ ์ํ TodoContext๋ผ๋ data box๋ฅผ ์ฌ์ฉํ  ์ ์๋ค`์ ์๋ฏธ)

  ```jsx
  import React from "react";
  import ReactDOM from "react-dom";
  import App from "./components/App";
  import ToDosProvider from "./context";

  ReactDOM.render(
    <ToDosProvider>
      <App />
    </ToDosProvider>,
    document.getElementById("root")
  );
  ```

  <br>

## ๐ค How to use Context with API

<br>

1. Context๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํ ์ค๋น!(Context๋ง๋ค๊ธฐ)

   ![image](https://user-images.githubusercontent.com/75834421/113894839-59920e00-9803-11eb-9540-7ee8bef0ff73.png)

   ```jsx
   // State ์ฉ Context ์ Dispatch ์ฉ Context ๋ฐ๋ก ๋ง๋ค์ด์ฃผ๊ธฐ
   const UsersStateContext = createContext(null);
   const UsersDispatchContext = createContext(null);

   // ์์์ ์ ์ธํ ๋๊ฐ์ง Context ๋ค์ Provider ๋ก ๊ฐ์ธ์ฃผ๋ ์ปดํฌ๋ํธ
   export function UsersProvider({ children }) {
     const [state, dispatch] = useReducer(usersReducer, initialState);
     return (
       <UsersStateContext.Provider value={state}>
         <UsersDispatchContext.Provider value={dispatch}>
           {children}
         </UsersDispatchContext.Provider>
       </UsersStateContext.Provider>
     );
   }

   // State ๋ฅผ ์ฝ๊ฒ ์กฐํ ํ  ์ ์๊ฒ ํด์ฃผ๋ ์ปค์คํ Hook
   export function useUsersState() {
     const state = useContext(UsersStateContext);
     if (!state) {
       throw new Error("Cannot find UsersProvider");
     }
     return state;
   }

   // Dispatch ๋ฅผ ์ฝ๊ฒ ์ฌ์ฉ ํ  ์ ์๊ฒ ํด์ฃผ๋ ์ปค์คํ Hook
   export function useUsersDispatch() {
     const dispatch = useContext(UsersDispatchContext);
     if (!dispatch) {
       throw new Error("Cannot find UsersProvider");
     }
     return dispatch;
   }
   ```

<br>

2.  API ์ฒ๋ฆฌ ํจ์ ๋ง๋ค๊ธฐ

    ```jsx
    import React, { createContext, useReducer, useContext } from "react";
    import axios from "axios";

    export async function getUsers(dispatch) {
      dispatch({ type: "GET_USERS" });
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/users"
        );
        dispatch({ type: "GET_USERS_SUCCESS", data: response.data });
      } catch (e) {
        dispatch({ type: "GET_USERS_ERROR", error: e });
      }
    }

    export async function getUser(dispatch, id) {
      dispatch({ type: "GET_USER" });
      try {
        const response = await axios.get(
          `https://jsonplaceholder.typicode.com/users/${id}`
        );
        dispatch({ type: "GET_USER_SUCCESS", data: response.data });
      } catch (e) {
        dispatch({ type: "GET_USER_ERROR", error: e });
      }
    }
    ```

     <br>

3.  Context ์ฌ์ฉํ๊ธฐ!

    ```jsx
    import React from "react";
    import Users from "./Users";
    import { UsersProvider } from "./UsersContext";

    function App() {
      return (
        <UsersProvider>
          <Users />
        </UsersProvider>
      );
    }

    export default App;
    ```

    <br>

4.  User์ Users component

    ![image](https://user-images.githubusercontent.com/75834421/113897269-aaa30180-9805-11eb-874a-94d49c948ffb.png)

    ์ฐธ๊ณ : <https://react.vlpt.us/integrate-api/05-using-with-context.html>

<br>

โญ ์ด๋ ๊ฒ Context๋ React์ ๊ฐ๋จํ ์ฑ ๋๋ API๋ก data๋ฅผ ๊ฐ์ ธ์์ ์ฌ์ฉํ  ๋ ์ ์ฉํฉ๋๋ค. ์ฌ๊ธฐ์ state ๋ ๋ง์์ง๊ณ , ๊ทธ state๋ฅผ ์์ฃผ ๋ฐ๊ฟ์ ๋์ฒดํด์ค์ผ ๋๋ค๋ฉด **Redux** ์ฌ์ฉ์ ์ถ์ฒ!
