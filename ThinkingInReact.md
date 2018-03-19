# Thinking in React

Start with a mock or wire frame of the page/app being built.

### Step 1: Break the UI into a Component Hierarchy

Draw boxes aroud each component/subcomponent and give them names. 
  - Define a component by the single responsibility rule- a component should only do one thing.

---

### Step 2: Build a Static Version

Build the app so that it takes a data model and renders the UI but with _no_ interactivity. Use props to pass data from the parent to the child but don't use state to build this (state is only for interactivity).

---

### Step 3: Identify the Minimal (but complete) Representation of UI State

Now add [state](https://github.com/nnguy152/react-cheatsheet/blob/master/states%26props.md).
 

---

### Step 4: Identify Where State Should Live

React is one-way data flow down the component hierarchy. 
For each piece of state in the app:

  - Identify every component that renders something based on state.
  - Find a common parent container.
  - That parent container, or one up, should own the state.
  - If you can't find one in common, make one just to hold the state.

---

### Add Inverse Data Flow

Update component state of the parent component by passing props into the contructor 

