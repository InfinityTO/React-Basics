# Context API - Avoiding Prop Drilling

## 📌 What is Context API?
React's **Context API** allows us to share state across components without passing props manually at every level. It helps avoid "prop drilling," where data has to be passed through multiple intermediate components.

---

## 📌 Understanding the Prop Drilling Problem
Prop drilling happens when a parent component passes data **deep down** to a child component through multiple intermediate components.

### ❌ Example - Prop Drilling Issue
```jsx
function App() {
  return <Parent user="John Doe" />;
}

function Parent({ user }) {
  return <Child user={user} />;
}

function Child({ user }) {
  return <GrandChild user={user} />;
}

function GrandChild({ user }) {
  return <h1>Hello, {user}!</h1>;
}
```
🔹 **Problem:** The `user` prop is unnecessarily passed through `Parent` and `Child`, even though only `GrandChild` needs it.

✅ **Solution:** Use **Context API** to share data directly with `GrandChild`.

---

## 📌 Creating and Using a Context
To solve prop drilling, we use **React Context API**:

### ✅ Step 1: Create a Context
```jsx
import React, { createContext } from "react";

// Create Context
const UserContext = createContext();
```

### ✅ Step 2: Provide Context in a Parent Component
```jsx
function App() {
  return (
    <UserContext.Provider value="John Doe">
      <Parent />
    </UserContext.Provider>
  );
}
```
🔹 **Explanation:**
- `UserContext.Provider` wraps the components and **provides** data (`value="John Doe"`).
- Any child component inside can access this value **without prop drilling**.

### ✅ Step 3: Consume Context in Any Component
```jsx
function GrandChild() {
  return (
    <UserContext.Consumer>
      {(user) => <h1>Hello, {user}!</h1>}
    </UserContext.Consumer>
  );
}
```
🔹 **Explanation:**
- `UserContext.Consumer` **subscribes** to context and receives the `user` value.

---

## 📌 Using `useContext` Hook (Recommended)
Instead of using `<Consumer>`, we can **use the `useContext` hook**, which makes the code cleaner.

### ✅ Example - Using `useContext`
```jsx
import React, { useContext } from "react";
import { UserContext } from "./UserContext";

function GrandChild() {
  const user = useContext(UserContext);
  return <h1>Hello, {user}!</h1>;
}
```
🔹 **Benefits of `useContext`**:
- No need for **Consumer wrapper**.
- Easier to read and maintain.

---

## 📌 When to Use Context API vs. Props?
| Scenario | Use Props | Use Context API |
|----------|----------|----------------|
| Passing data to **a few** components | ✅ Yes | ❌ No |
| Avoiding prop drilling | ❌ No | ✅ Yes |
| Sharing global state (e.g., theme, auth) | ❌ No | ✅ Yes |

🔹 **Best Practice:** Use props for **local state** and Context API for **global/shared state**.

---

## ✅ Summary
✔️ Context API prevents unnecessary **prop drilling**.  
✔️ `createContext()` and `Provider` **share** state across components.  
✔️ `useContext()` is a cleaner way to access context.  
✔️ Use Context API for **global state**, but prefer props for simple data passing.  

🚀 Now you can efficiently manage **shared state** in React applications! 🎯

