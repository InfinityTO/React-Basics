# Error Boundaries in React

Error handling is a crucial aspect of building reliable React applications. React provides a way to handle JavaScript errors in components using **Error Boundaries**.

## 🔹 What are Error Boundaries?
Error Boundaries are special React components that catch JavaScript errors anywhere in their child component tree and log those errors instead of crashing the whole application. They help prevent unhandled errors from affecting the entire UI.

### Key Features of Error Boundaries:
- Catches errors during **rendering, lifecycle methods, and constructors** of child components.
- Displays a fallback UI instead of crashing the entire app.
- Does **not** catch errors inside event handlers.

## 🔹 How to Create an Error Boundary
Error Boundaries are implemented using **class components**. A component qualifies as an Error Boundary if it defines either (or both) of these lifecycle methods:

- `static getDerivedStateFromError(error)`: Updates the state when an error occurs.
- `componentDidCatch(error, info)`: Logs error details.

### ✅ Example: Creating an Error Boundary Component
```jsx
import React, { Component } from "react";

class ErrorBoundary extends Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    console.error("Error caught by Error Boundary:", error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <h2>Something went wrong.</h2>;
    }
    return this.props.children;
  }
}

export default ErrorBoundary;
```

## 🔹 Using an Error Boundary in an Application
To use an Error Boundary, wrap the components that might throw an error inside it.

```jsx
import React from "react";
import ErrorBoundary from "./ErrorBoundary";
import BuggyComponent from "./BuggyComponent";

function App() {
  return (
    <ErrorBoundary>
      <BuggyComponent />
    </ErrorBoundary>
  );
}

export default App;
```

## 🔹 Example: A Component That Triggers an Error
```jsx
import React, { useState } from "react";

function BuggyComponent() {
  const [count, setCount] = useState(0);

  if (count > 3) {
    throw new Error("Count exceeded safe limit!");
  }

  return (
    <div>
      <h3>Click the button to increase the count:</h3>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </div>
  );
}

export default BuggyComponent;
```

## 🔹 When to Use Error Boundaries?
Use Error Boundaries around:
- **Components fetching data** from APIs.
- **Third-party UI components**.
- **Complex UI sections** where failures shouldn’t break the entire app.

## 🔹 Limitations of Error Boundaries
- They **do not** catch errors inside **event handlers**.
- They **do not** catch errors in asynchronous code (e.g., inside `setTimeout` or `fetch`).
- They **do not** catch errors in server-side rendering.

## 🔹 Summary
✔ **Error Boundaries** prevent the entire app from crashing due to errors in components.
✔ They are implemented using **class components** with `componentDidCatch` and `getDerivedStateFromError`.
✔ Wrap components inside an **ErrorBoundary** to gracefully handle errors.

By implementing Error Boundaries, you can create more resilient and user-friendly React applications! 🚀

