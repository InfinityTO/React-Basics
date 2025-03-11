# Understanding useEffect in React

React introduced Hooks in version 16.8, allowing functional components to use state and lifecycle features previously available only in class components. One of the most essential hooks is `useEffect`, which helps manage side effects in React applications.

---

## 📌 What are Hooks in React?
Hooks are functions that let you "hook into" React state and lifecycle features from functional components. The most common hooks include `useState` for managing state and `useEffect` for handling side effects like fetching data, updating the DOM, or setting up subscriptions.

---

## 📌 What is the `useEffect` Hook?
The `useEffect` Hook allows you to perform side effects in functional components. Side effects can include:
- Fetching data from an API
- Subscribing to events
- Updating the document title
- Running code after component render

`useEffect` runs after the component renders and can be controlled with dependencies to execute only when needed.

---

## 📌 Basic Syntax and Usage
```jsx
import React, { useState, useEffect } from "react";

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Component rendered or updated!");
  });

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increase Count</button>
    </div>
  );
}

export default Example;
```
🔹 **Explanation:**
- `useEffect` runs after every render.
- The effect logs a message to the console whenever the component updates.

---

## 📌 Running Effects Only Once (Dependency Array)
To run `useEffect` only once (on mount), pass an empty dependency array `[]`.

```jsx
useEffect(() => {
  console.log("Component mounted!");
}, []); // Runs only on mount
```
🔹 **Explanation:**
- The empty array ensures the effect runs **only once**, similar to `componentDidMount` in class components.

---

## 📌 useEffect with Dependencies
You can specify dependencies in the array to control when `useEffect` runs.

```jsx
useEffect(() => {
  console.log(`Count updated: ${count}`);
}, [count]);
```
🔹 **Explanation:**
- The effect runs **only when** `count` changes.
- Useful for responding to state or prop changes.

---

## 📌 Cleaning Up Effects
When using effects like event listeners or API calls, it's important to clean up resources.

```jsx
useEffect(() => {
  const handleResize = () => console.log("Window resized");
  window.addEventListener("resize", handleResize);

  return () => {
    window.removeEventListener("resize", handleResize);
    console.log("Cleanup on unmount!");
  };
}, []);
```
🔹 **Explanation:**
- The cleanup function **removes the event listener** when the component unmounts.
- Prevents memory leaks.

---

## ✅ Summary
1. `useEffect` handles side effects in functional components.
2. Runs after every render **by default**.
3. Can be controlled using a **dependency array**.
4. Can run **only once on mount** by passing `[]`.
5. Cleaning up effects is essential to avoid memory leaks.

With `useEffect`, you can manage component lifecycles efficiently in functional components! 🚀

