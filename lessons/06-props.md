# Lesson 6: Props - Passing Data to Components

## 📌 What are Props in React?
**Props** (short for "properties") are used to pass data from a **parent component** to a **child component** in React. They help make components reusable and dynamic.

Think of props like **function parameters**—they allow us to customize a component’s behavior.

---

## 🔹 How Props Work
Props are **read-only** and passed as attributes to a child component.

### **Example: Passing Props to a Child Component**
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Welcome name="Alice" />;
}

export default App;
```
🔹 Here, `name="Alice"` is passed as a **prop** from `<App />` to `<Welcome />`, and it gets displayed as `Hello, Alice!`.

---

## 🔹 Props Are Immutable
Props **cannot be changed** inside a component. If you try to modify `props`, React will throw an error.

#### ❌ Incorrect Example:
```jsx
function Welcome(props) {
  props.name = "Bob"; // ❌ This will cause an error!
  return <h1>Hello, {props.name}!</h1>;
}
```
🔹 Instead, use **state** if you need to change data inside a component.

---

## 🔹 Destructuring Props
Instead of using `props.name`, we can **destructure** props inside the function parameter.

### ✅ Better Approach:
```jsx
function Welcome({ name }) {
  return <h1>Hello, {name}!</h1>;
}
```
🔹 This makes the code cleaner and easier to read.

---

## 🔹 Passing Multiple Props
We can pass multiple props just like function arguments.

### **Example: Passing Multiple Props**
```jsx
function UserInfo({ name, age }) {
  return (
    <p>
      {name} is {age} years old.
    </p>
  );
}

function App() {
  return <UserInfo name="Alice" age={25} />;
}
```
🔹 Here, both `name` and `age` are passed as props and used inside `<UserInfo />`.

---

## 🔹 Default Props
We can define **default props** for when a prop is not provided.

### **Example: Using Default Props**
```jsx
function Welcome({ name = "Guest" }) {
  return <h1>Hello, {name}!</h1>;
}

function App() {
  return <Welcome />; // Outputs: Hello, Guest!
}
```
🔹 Since no `name` prop is passed, it defaults to `"Guest"`.

---

## ✅ Summary
1. **Props** are used to pass data from parent to child components.
2. Props are **immutable** (read-only).
3. We can **destructure props** to simplify the code.
4. **Multiple props** can be passed to a component.
5. **Default props** provide fallback values when props are missing.

This lesson covered **everything a beginner needs to know about props** in React! 🚀

