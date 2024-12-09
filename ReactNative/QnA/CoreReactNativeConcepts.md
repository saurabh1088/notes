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
- Key methods in updating phase
    - `static getDerivedStateFromProps(nextProps, prevState)`
        - Same as in the mounting phase, also called during updates.
        - This method gets called whenever any changes occurred in state or props.
    - `shouldComponentUpdate(nextProps, nextState)`
        - Determines whether the component should re-render.
        - Returns true (default) or false.
        - Useful for optimizing performance.
        - Doesn't gets called on initial render or when forceUpdate is used.
        - To stop re-rendering on changing state or props, one should return false.
    - `render()`
        - Same as in the mounting phase.
        - Whenever there is any change in the state or props then render methods gets called again.
    - `getSnapshotBeforeUpdate(prevProps, prevState)`
        - Captures information from the DOM before changes are applied.
        - Returns a value passed to componentDidUpdate.
    - `componentDidUpdate(prevProps, prevState, snapshot)`
        - Called after the component has been updated.
        - Ideal for performing DOM operations or further updates based on changes.

### 1.3 Unmounting
- In this phase, a react component gets removed from actual DOM.
- Key methods in unmounting phase
    - `componentWillUnmount()`
        - Gets invoked when component is removed from the DOM.
        - Called immediately before a component is unmounted.
        - Ideal for cleanup tasks like canceling API calls, removing event listeners, or invalidating timers.

### 1.4 Error Handling
- It is called when any error occurs while rendering the component.
- Key methods in error handling phase
    - `static getDerivedStateFromError()`
        - It is called whenever any error occurred while rendering.
        - It receives the error as a parameter and returns the value to update the state.
    - `componentDidCatch()`
        - Invoked when any error is thrown by descendant component.
        - Receives error and info objects.
        - Info object received has information about which component threw that error.



