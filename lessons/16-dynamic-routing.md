# Dynamic Routing with React Router

Dynamic routing allows you to handle different routes dynamically based on user input, URL parameters, or state. React Router provides powerful tools like `useParams`, query parameters, and nested routes to make dynamic routing easier.

---

## 📌 What is Dynamic Routing?
Dynamic routing enables rendering different components based on **route parameters**. It allows handling dynamic content, such as user profiles (`/users/:id`), product details (`/products/:productId`), or blog posts (`/blog/:slug`).

---

## 📌 Setting Up Route Parameters
We can define **dynamic routes** in `react-router-dom` using a colon (`:`) followed by a parameter name inside the `path`.

### ✅ Example - Defining a Dynamic Route
```jsx
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import UserProfile from "./UserProfile";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/users/:id" element={<UserProfile />} />
      </Routes>
    </Router>
  );
}

export default App;
```
🔹 **Explanation:**
- `path="/users/:id"` means `id` is a dynamic parameter.
- Any URL like `/users/123` or `/users/abc` will match this route.
- The `UserProfile` component will be rendered when the route matches.

---

## 📌 Accessing Route Parameters with `useParams`
React Router provides the `useParams` hook to retrieve dynamic parameters from the URL inside a component.

### ✅ Example - Using `useParams`
```jsx
import { useParams } from "react-router-dom";

function UserProfile() {
  let { id } = useParams();
  return <h2>User Profile for ID: {id}</h2>;
}

export default UserProfile;
```
🔹 **Explanation:**
- `useParams()` returns an object containing route parameters.
- The `{id}` value dynamically changes based on the URL.
- If the URL is `/users/5`, the component displays `User Profile for ID: 5`.

---

## 📌 Nested Routes in Dynamic Routing
You can create **nested routes** to display different components inside a parent route.

### ✅ Example - Nested Routes
```jsx
import { Routes, Route, Outlet } from "react-router-dom";

function Users() {
  return (
    <div>
      <h2>Users List</h2>
      <Outlet /> {/* Renders nested routes */}
    </div>
  );
}

function UserDetail() {
  let { id } = useParams();
  return <h3>Details for User {id}</h3>;
}

function App() {
  return (
    <Routes>
      <Route path="users" element={<Users />}>
        <Route path=":id" element={<UserDetail />} />
      </Route>
    </Routes>
  );
}
```
🔹 **Explanation:**
- The `Outlet` component renders nested routes inside the `Users` component.
- Visiting `/users/3` will render `UserDetail` inside `Users`.

---

## 📌 Query Parameters & URL Search Params
Sometimes, you need to extract query parameters from the URL. You can use the `useSearchParams` hook.

### ✅ Example - Using Query Parameters
```jsx
import { useSearchParams } from "react-router-dom";

function SearchPage() {
  let [searchParams] = useSearchParams();
  let keyword = searchParams.get("q");
  return <h2>Search results for: {keyword}</h2>;
}
```
🔹 **Explanation:**
- If the URL is `/search?q=react`, the component displays `Search results for: react`.
- `useSearchParams()` extracts query parameters from the URL.

---

## 📌 Handling 404 Pages for Invalid Routes
To handle invalid routes, define a `*` wildcard route to display a custom **404 Page Not Found** component.

### ✅ Example - Handling 404 Routes
```jsx
function NotFound() {
  return <h2>404 - Page Not Found</h2>;
}

function App() {
  return (
    <Routes>
      <Route path="*" element={<NotFound />} />
    </Routes>
  );
}
```
🔹 **Explanation:**
- `path="*"` matches all undefined routes.
- When a user visits an invalid URL, the `NotFound` component is displayed.

---

## ✅ Summary
1. **Dynamic Routing** enables handling different URLs dynamically using route parameters.
2. **useParams** extracts dynamic parameters from the URL.
3. **Nested Routes** allow structuring routes inside parent components.
4. **Query Parameters** can be retrieved using `useSearchParams`.
5. **404 Handling** ensures users see a friendly error page for undefined routes.

Mastering dynamic routing makes your React applications more flexible and user-friendly! 🚀

