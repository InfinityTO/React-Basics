# The useReducer Hook in React

The `useReducer` hook is an alternative to `useState` for managing more complex state logic in React functional components. It provides a way to handle state transitions in a structured manner.

---

## 📌 What is the useReducer Hook?
The `useReducer` hook is a built-in React hook that is used for managing state in functional components. It is particularly useful when the state logic involves multiple sub-values or complex state transitions.

### ✅ Basic Syntax
```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```
- **`reducer`**: A function that determines state changes based on an action.
- **`initialState`**: The initial value of the state.
- **`dispatch`**: A function that triggers state updates.

---

## 📌 When to Use useReducer vs useState
Use `useReducer` when:
- The state logic is complex and involves multiple sub-values.
- The next state depends on the previous state.
- You want a more predictable state update structure (similar to Redux).

Use `useState` when:
- The state logic is simple and doesn't involve many transitions.
- The component does not require centralized state management.

---

## 📌 How useReducer Works (Simple Counter Example)
Let's implement a simple counter using `useReducer`.

### ✅ Example - Counter with useReducer
```jsx
import React, { useReducer } from "react";

// Reducer function
toggle const counterReducer = (state, action) => {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "reset":
      return { count: 0 };
    default:
      return state;
  }
};

function Counter() {
  const [state, dispatch] = useReducer(counterReducer, { count: 0 });

  return (
    <div>
      <h2>Count: {state.count}</h2>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
    </div>
  );
}

export default Counter;
```
🔹 **Explanation:**
- The `counterReducer` function updates the state based on the `action.type`.
- The `dispatch` function is used to trigger state updates by passing an action object.
- The state is an object with a `count` property that updates based on user actions.

---



## 📌 Using useReducer with useContext (Global State Management)
When used with `useContext`, `useReducer` can manage global state effectively.

### ✅ Example - Global Theme Toggle
```jsx
import React, { useReducer, createContext, useContext } from "react";

// Create context
const ThemeContext = createContext();

// Reducer function
const themeReducer = (state) => {
  return state === "light" ? "dark" : "light";
};

function ThemeProvider({ children }) {
  const [theme, dispatch] = useReducer(themeReducer, "light");
  return (
    <ThemeContext.Provider value={{ theme, dispatch }}>
      {children}
    </ThemeContext.Provider>
  );
}

function ThemeToggleButton() {
  const { theme, dispatch } = useContext(ThemeContext);
  return (
    <div style={{ background: theme === "light" ? "#fff" : "#333", color: theme === "light" ? "#000" : "#fff", padding: "20px" }}>
      <p>Current Theme: {theme}</p>
      <button onClick={() => dispatch()}>Toggle Theme</button>
    </div>
  );
}

function App() {
  return (
    <ThemeProvider>
      <ThemeToggleButton />
    </ThemeProvider>
  );
}

export default App;
```
🔹 **Explanation:**
- `useReducer` toggles the theme between `"light"` and `"dark"`.
- `useContext` provides global access to the theme state.
- Clicking the button toggles the theme across the app.

---

## ✅ Summary
1. `useReducer` is useful for managing complex state logic.
2. It works by dispatching actions to modify state based on a reducer function.
3. It is preferable over `useState` for state logic with multiple transitions.
4. It can be combined with `useContext` for global state management.

Mastering `useReducer` helps in building scalable and maintainable React applications! 🚀

