# Custom Hooks in React

## 🔹 What are Custom Hooks?
Custom Hooks are reusable functions that allow you to extract and share logic between multiple components in a React application. They enable better code organization and avoid redundancy when dealing with stateful logic.

### 📝 Why Use Custom Hooks?
- **Code Reusability**: Helps avoid code duplication.
- **Separation of Concerns**: Keeps components clean and focused.
- **Improved Readability**: Extracts complex logic into reusable functions.
- **Easy to Test**: Custom Hooks can be tested separately.

## 🔹 Creating a Custom Hook
A Custom Hook is simply a JavaScript function that starts with `use` and can use other React Hooks inside it.

### ✨ Example: Creating a `useCounter` Hook
```jsx
import { useState } from "react";

function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  const increment = () => setCount(count + 1);
  const decrement = () => setCount(count - 1);
  const reset = () => setCount(initialValue);

  return { count, increment, decrement, reset };
}

export default useCounter;
```

### 🛠 Using `useCounter` in a Component
```jsx
import React from "react";
import useCounter from "./useCounter";

function CounterComponent() {
  const { count, increment, decrement, reset } = useCounter(10);

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
      <button onClick={reset}>Reset</button>
    </div>
  );
}

export default CounterComponent;
```

## 🔹 Handling Side Effects with Custom Hooks
If your Custom Hook involves side effects, you can use the `useEffect` hook.

### ✨ Example: `useFetch` Hook for API Calls
```jsx
import { useState, useEffect } from "react";

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    async function fetchData() {
      try {
        const response = await fetch(url);
        const result = await response.json();
        setData(result);
      } catch (err) {
        setError(err);
      } finally {
        setLoading(false);
      }
    }
    fetchData();
  }, [url]);

  return { data, loading, error };
}

export default useFetch;
```

### 🛠 Using `useFetch` in a Component
```jsx
import React from "react";
import useFetch from "./useFetch";

function DataComponent() {
  const { data, loading, error } = useFetch("https://jsonplaceholder.typicode.com/posts/1");

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <div>
      <h2>{data.title}</h2>
      <p>{data.body}</p>
    </div>
  );
}

export default DataComponent;
```

## 🔹 Best Practices for Custom Hooks
✔ **Start Hook names with `use`** (e.g., `useTheme`, `useAuth`).

✔ **Extract only necessary logic** (keep it simple and focused).

✔ **Use existing hooks inside Custom Hooks** (like `useState`, `useEffect`).

✔ **Return only relevant values/functions**.

✔ **Ensure reusability** (avoid component-specific logic).


## 🔹 Summary
✅ Custom Hooks help in reusing logic across components.

✅ They enhance readability and maintainability.

✅ Can encapsulate both state and side effects.

✅ Follow best practices to keep them efficient and reusable.


---
🔥 Now you can create your own Custom Hooks and enhance your React projects! 🚀

