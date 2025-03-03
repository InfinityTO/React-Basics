# React Components - The Building Blocks

In React, **components** are the fundamental building blocks of any application. A component is a reusable piece of UI that can be independent and self-contained. React applications are built by composing multiple components together.

---

## 📌 Why Use Components?

- **Reusability**: Components can be reused across different parts of the application.
- **Maintainability**: Code is easier to manage when split into smaller, modular components.
- **Readability**: The structure of the application is more organized and easier to understand.
- **Scalability**: Large applications can be built by composing small components together.

---

## 📌 Types of Components

There are two main types of React components:

### 1️⃣ Functional Components
- **Simpler and more modern**
- Written as JavaScript functions
- Use hooks (like `useState` and `useEffect`) for state and lifecycle management
- **Preferred way** to write components in React today

#### Example:
```jsx
function Greeting() {
  return <h1>Hello, welcome to React!</h1>;
}

export default Greeting;
```

### 2️⃣ Class Components (Older Approach)
- Used before React Hooks were introduced
- Written as ES6 classes
- Use lifecycle methods like `componentDidMount()`

#### Example:
```jsx
import React, { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, welcome to React!</h1>;
  }
}

export default Greeting;
```

> **Note:** Class components are still supported but are not commonly used in modern React applications.

---

## 📌 Component Composition

Components can be combined to create complex UIs. A **parent component** can include multiple **child components**.

#### Example:
```jsx
function Header() {
  return <h1>My Website</h1>;
}

function Footer() {
  return <p>Copyright 2025</p>;
}

function App() {
  return (
    <div>
      <Header />
      <p>Welcome to my site!</p>
      <Footer />
    </div>
  );
}

export default App;
```

---

## ✅ Summary

1. **Components** are the building blocks of a React app.
2. There are **two types**: **Functional Components** (modern) and **Class Components** (older).
3. **Functional Components** are preferred in modern React.
4. Components can be **nested and composed** to create reusable UIs.

This is the foundation of React development! 🚀
