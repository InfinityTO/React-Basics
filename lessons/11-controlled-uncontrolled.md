# Controlled vs Uncontrolled Components in React

In React, form inputs can be managed in two ways: **controlled components** and **uncontrolled components**. Understanding the difference is essential for handling user input effectively.

---

## 📌 What are Controlled Components?

A **controlled component** is a form element whose value is controlled by React state. This means React is responsible for updating and maintaining the input's value.

### ✅ Example - Controlled Input
```jsx
import React, { useState } from "react";

function ControlledInput() {
  const [text, setText] = useState("");

  function handleChange(event) {
    setText(event.target.value);
  }

  return (
    <div>
      <input type="text" value={text} onChange={handleChange} />
      <p>Typed Text: {text}</p>
    </div>
  );
}

export default ControlledInput;
```
🔹 **Explanation:**
- The `value` of the `<input>` is linked to the `text` state.
- The `onChange` handler updates the state whenever the user types.
- React fully controls the input’s value.

---

## 📌 What are Uncontrolled Components?

An **uncontrolled component** is a form input where React does not manage the state. Instead, the input’s value is handled by the DOM itself, and you access it using a `ref`.

### ✅ Example - Uncontrolled Input
```jsx
import React, { useRef } from "react";

function UncontrolledInput() {
  const inputRef = useRef(null);

  function handleSubmit(event) {
    event.preventDefault();
    alert(`Entered Text: ${inputRef.current.value}`);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={inputRef} />
      <button type="submit">Submit</button>
    </form>
  );
}

export default UncontrolledInput;
```
🔹 **Explanation:**
- The `ref` is assigned to the `<input>` field.
- The value is accessed using `inputRef.current.value` when needed.
- React does not control the state of the input.

---

## 📌 When to Use Controlled vs Uncontrolled Components?

| Feature                | Controlled Components | Uncontrolled Components |
|-----------------------|----------------------|------------------------|
| **State Management**  | Managed by React    | Managed by the DOM    |
| **Use Case**          | Form validation, dynamic updates | Simple forms, integrating with non-React code |
| **Performance**       | Can be slower for large forms | Faster for simple uncontrolled inputs |
| **Complexity**        | More code but predictable | Simpler but harder to manage |

---

## ✅ Summary

1. **Controlled components** use state (`useState`) to manage input values.
2. **Uncontrolled components** rely on the DOM and `ref` for value access.
3. Controlled components provide better validation and control but require more code.
4. Use uncontrolled components for simple cases where state management is unnecessary.

Mastering these concepts helps in handling forms efficiently in React! 🚀

