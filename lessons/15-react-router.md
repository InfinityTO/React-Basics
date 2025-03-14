# React Router - Navigation Basics

## 📌 Introduction to React Router
React Router is a popular library that enables navigation and routing in React applications. It allows users to switch between different pages (components) without reloading the entire application.

### ✅ Why Use React Router?
- Enables **single-page application (SPA)** navigation.
- Provides **dynamic routing** based on URL.
- Allows handling of **nested routes** and **route parameters**.
- Improves **user experience** by reducing full-page reloads.

---

## 📌 Setting Up React Router
To use React Router, install it using npm or yarn:
```sh
npm install react-router-dom
```

Import necessary components from `react-router-dom` in your main file (e.g., `index.js` or `App.js`).

### ✅ Example - Basic Setup
```jsx
import React from "react";
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";

function Home() {
  return <h2>Home Page</h2>;
}

function About() {
  return <h2>About Page</h2>;
}

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}

export default App;
```

🔹 **Explanation:**
- `BrowserRouter` (`Router`) wraps the app to enable routing.
- `Link` component provides navigation links without refreshing the page.
- `Routes` acts as a container for different `Route` components.
- Each `Route` defines a specific path and the component to render.

---

## 📌 Navigating with `useNavigate`
Instead of `Link`, we can programmatically navigate using `useNavigate`.

### ✅ Example - Using `useNavigate`
```jsx
import { useNavigate } from "react-router-dom";

function Home() {
  const navigate = useNavigate();
  
  function goToAbout() {
    navigate("/about");
  }
  
  return (
    <div>
      <h2>Home Page</h2>
      <button onClick={goToAbout}>Go to About</button>
    </div>
  );
}
```

🔹 **Explanation:**
- `useNavigate` hook is used for navigation inside functions.
- `navigate("/about")` redirects the user to the About page.

---

## 📌 Handling 404 Pages (Not Found Routes)
You can create a fallback route using `*` (wildcard).

### ✅ Example - 404 Page
```jsx
function NotFound() {
  return <h2>404 - Page Not Found</h2>;
}

<Route path="*" element={<NotFound />} />
```

🔹 **Explanation:**
- If no route matches, `NotFound` component is displayed.

---

## ✅ Summary
1. **React Router** enables navigation in React apps.
2. Use `Router`, `Routes`, and `Route` for defining paths.
3. **`Link`** provides in-app navigation.
4. **`useNavigate`** allows programmatic redirection.
5. Handle 404 pages using `*` wildcard routes.

With React Router, you can build seamless, dynamic SPAs! 🚀

