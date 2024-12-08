#  Core React Native Concepts


## 1. Explain the different lifecycle methods in React Native and when they are used.
- React Native components follow a lifecycle that mirrors React components since React Native is built on React.
    - TODO: Check the React lifecycle methods.
- Understanding these lifecycle methods helps manage state, handle events, and perform side effects in an app.
- A component’s life cycle in React Native can be divided into 4 phases
    - Mounting
    - Updating
    - Unmounting
    - Error Handling

### 1.1 Mounting
- In this phase, component instance is created and inserted into the DOM(or the native UI for React Native).
- Key methods in mounting phase
    - `constructor()`
        - First method which gets called in the lifecycle of react native component.
        - Used to initialise the component with initial state.
        - Called before the component is mounted.
        - Commonly used for initializing the state or binding methods.
        - One should avoid API calls here.
    - `static getDerivedStateFromProps(nextProps, prevState)`
        - Invoked before rendering when new props or state are received.
        - Returns an object to update state or null to update nothing.
        - Rarely used instead `useEffect` or similar hooks in functional components are preferred approaches.
    - `render()`
        - Only required method in react component.
        - It tells what to display on the screen.
        - Returns the JSX to be displayed.
        - It's a pure function, means it doesn't modify state.
        - Returns the same result each time it is invoked.
        - Does not directly interact with the browser.
    - `componentDidMount()`
        - Called immediately after the component is mounted.
        - Ideal for API calls, setting up subscriptions, state update, or initial DOM/native operations.
        - This will refresh the UI of our mobile screen.

### 1.2 Updating
- In updating phase, a react component is said to be born and it start growing by receiving new updates.
- This phase occurs when a component's state or props change.
- Key methods in mounting phase
    - `static getDerivedStateFromProps(nextProps, prevState)`

### 1.3 Unmounting
- In this phase, a react component gets removed from actual DOM.

### 1.4 Error Handling
- It is called when any error occurs while rendering the component.


