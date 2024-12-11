#  Core React Native Concepts


## 🙋‍♂️1. Explain the different lifecycle methods in React Native and when they are used.
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


## 🙋‍♂️2. Describe JSX syntax and its benefits in React Native.
- JSX(JavaScript XML) is an extension syntax for JavaScript, popularized by React and used in React Native development.
- It allows one to write HTML-like code within JavaScript, making it easier to describe UI structures.
- JSX produces React elements.

### 2.1 Why JSX is required?
- First thing, Reach DOES NOT require using JSX.
- React embraces the fact that rendering logic is inherently coupled with other UI logic.
- So instead of trying to separate technologies by putting markup and logic in separate files, React separates concerns
with loosely coupled units called components that contain both.
- So most people will find it helpful as a visual aid when working with UI inside the JavaScript code.
-  It also allows React to show more useful error and warning messages.

### 2.2 Benefits of JSX in React Native

#### 2.2.1 Clarity and Readability:
- JSX makes the structure of UI components more intuitive and similar to HTML, which is familiar to many developers.
- This visual similarity aids in understanding the component hierarchy at a glance.
#### 2.2.2 Performance:
- The compilation of JSX into JavaScript function calls allows React to optimize rendering by minimizing DOM manipulation.
- In React Native, this translates to more efficient updates to the native view tree.
#### 2.2.3 Type Safety with TypeScript:
- When used with TypeScript, JSX can provide type-checking for props, which helps catch errors during development rather
than at runtime.
#### 2.2.4 Modularity and Reusability:
- JSX encourages component-based architecture where each piece of the UI can be a modular, reusable component.
- This modular approach is central to React Native's philosophy.
#### 2.2.5 Integration with JavaScript:
- By blending HTML-like syntax with JavaScript, one can handle logic and UI in one place, reducing the separation between
behavior and appearance.
- This integration is particularly beneficial in mobile development where one might need to respond to device-specific
events or use native APIs.
#### 2.2.6 Easier Debugging:
- Since JSX is transformed into JavaScript calls, one can use standard JavaScript debugging tools, making it easier to
step through the code where UI and logic meet.
#### 2.2.7 Better Developer Experience:
- Many IDEs and text editors support JSX with syntax highlighting, auto-completion, and live previews, which enhances
development speed and reduces errors.
#### 2.2.8 Expressive and Concise:
- JSX allows developers to express UI in a way that's both descriptive and concise, reducing the cognitive load of mapping
back and forth between UI design and implementation.
#### 2.2.9 Encourages Declarative Programming:
- JSX fosters a declarative style where you describe what the UI should look like given certain props, rather than
imperatively manipulating the UI.


