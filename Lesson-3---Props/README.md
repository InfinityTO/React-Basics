# Lesson 3: Props --> Passing Data to Components in React 🚀
Props (short for "properties") are one of the most important features in React, allowing you to pass data between components. In this lesson, we will explore how to use props to make your components dynamic and reusable. You'll learn how to pass data from a parent component to a child component and use that data in the child component.
## 1. What are Props?
Props are a way to pass data from one component to another in React. They are immutable and are passed down from a parent component to a child component.
### Key Points:
- Props are `read-only`: They cannot be changed by the child component.
- Props allow us to create `dynamic` content in our react app.
- Every component can access the props passed to it.

## 2. Data Flow Between Two Components
    
When two components communicate with each other, the one sending the props data is known as `Parent Component` and the one receiving the props data is called `Child Component` 
    
This parent-child relationship allows parent to pass down data to child components using props.