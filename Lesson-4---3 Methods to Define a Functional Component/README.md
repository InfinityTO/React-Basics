# 3 Methods to Define a Functional Component in React 🚀

## Introduction
In React, functional components are the most common way to create reusable UI elements. A functional component is simply a JavaScript function that returns JSX (a special syntax that looks like HTML).

In this lesson, we will explore three different ways to define a functional component in React:

_**1. Regular Function (Function Declaration)**_

_**2. Arrow Function (Function Expression)**_

_**3. Anonymous Function (Nameless Function)**_

Let's dive into each method with simple examples.

## 1. Regular Function (Function Declaration)
The most basic way to define a functional component is by using a regular function.

### Example:
```
function Welcome() {
  return <h1>Hello, Welcome to React!</h1>;
}

export default Welcome;
```

### Explanation:
* We define a function named `Welcome`.
* It returns a JSX element (`<h1>`), which will be displayed on the screen.
* Finally, we export the component so it can be used in other parts of our app.

## 2. Arrow Function (Function Expression)
A more modern way to define components is by using an arrow function.

### Example:
```
const Welcome = () => {
  return <h1>Hello, Welcome to React!</h1>;
};

export default Welcome;
```

### Explanation:
* Instead of `function`, we use the arrow function syntax (`const Welcome = () => {}`).
* The rest of the code is the same: it returns JSX.
* This method is often preferred because it makes the code shorter and cleaner.

## 3. Anonymous Function (Nameless Function)
This function does not have a name, so it's called an anonymous function. But is less commonly used in modern React.
### Example
```
const Welcome = function () {
  return <h1>Hello, Welcome to React!</h1>;
};

export default Welcome;
```

### Explanation:
* Instead of using a function declaration (`function Welcome() {}`), the function is assigned to a variable (`const Welcome`).
* Since it's stored in a variable, the variable name (`Welcome`) acts as the component's identifier.

## Conclusion
Now you know three ways to define a functional component in React! 🚀 Start with any method that feels comfortable, but the **_arrow function_** approach is recommended for modern React development.
