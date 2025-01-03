# Lesson 2: How to Create Your First React Component 🚀
This lesson explains how to create a React component, use it within your app, and understand its importance in building modular and reusable UI elements.

## 1. What is a React Component?
A React component is a reusable piece of UI that is defined using JavaScript. Components make your application modular, allowing you to build complex UIs by combining simple building blocks.

### Types of Components:
1. **Functional Components:** These are JavaScript functions that return JSX.
2. **Class Components:** These are ES6 classes that extend React.Component. (We’ll focus on functional components for now as they are more commonly used today.)

## 2. Create Your First Functional Component
### Steps:
1. Open Your React App: Navigate to the folder of your React app if it’s not already open:

```
cd firstapp
```
2. Create a New Component File:

- Inside the `src` folder, create a new file named `MyComponent.js`
3. Write Your First Component: Open `MyComponent.js` and add the following code:

```
import React from 'react';

function MyComponent() {
  return (
    <div>
      <h2>Hello from MyComponent!</h2>
      <p>This is my first custom React component. 🎉</p>
    </div>
  );
}

export default MyComponent;
```

4. Explanation:

- `import React from 'react';`: React must be imported to use JSX.

- `function MyComponent()`: This defines the component.

- `return (...)`: Specifies what the component renders (JSX).

## 3. Use Your Component in the App
To display your new component in the main app:

### Steps:

1. Open `App.js` : This is the root component of your app.

2. Import `MyComponent`: Add this line at the top:

```
import MyComponent from './MyComponent';
```

3. Use the Component in JSX: Replace the default content in the return statement with:

```
function App() {
  return (
    <div className="App">
      <h1>Welcome to React Basics!</h1>
      <MyComponent />
    </div>
  );
}

export default App;
```

4. Save and Run: Save the changes and run the app:

```
npm start
```

You should see:
 - "Welcome to React Basics!" from the `App` component.
 - "Hello from MyComponent!" heading from `MyComponent`
 - "This is my first custom React component. 🎉" and also paragraph from `MyComponent`

## 4. Best Practices for Components

1. Name Files Consistently:
  - Use PascalCase for component files (e.g., `MyComponent.js`).

2. Keep Components Small:
- Each component should ideally represent a single piece of UI or logic.
3. Use Reusable Logic:
- Components can be reused across different parts of the app.

## 5. Key Concepts Introduced
**1. Functional Components:**

 - Simple JavaScript functions that return JSX.
Example: `MyComponent`

**2. Component Hierarchy:**

- Components can contain other components. For example, App contains MyComponent.

**3. Reusability:**

- Once created, a component can be reused multiple times in different places.

## 6. Resources
1. [React Components Documentation](https://react.dev/reference/react/Component)

2. [JSX Syntax](https://react.dev/learn/writing-markup-with-jsx)


This completes Lesson 2! 🎉