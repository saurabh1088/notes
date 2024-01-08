#  ReactNative

- React Native is an open-source Framework which was developed by FaceBook. 
- React Native enables one to build mobile applications using JavaScript and React. Aim here is to create cross-platform 
applications which can run both on iOS and Android platforms sharing a huge chunk of codebase.
- Code is written in JavaScript and further rendered with native code.
- React Native provides native components which map directly to target platform's native ones.
- Similar to concept of views in iOS and Android, React Native also has views as the basic building blocks of user interface.
- Everything seen on the UI boils down to a view.
- React Native comes with some *Core Components* which are ready to use components for builiding UI. One can also build custom
native components.

## React Native UI Components

<View>
<Text>
<Image>
<ScrollView>
<TextInput>

### <Pressable>

To make a componenet react to press events one needs to wrap it inside <Pressable> component. Then we can provide a function
to call like below :

```
<Pressable onPress={someFunctionHandlingEvent}>
    <Text>Some Text</Text>
</Pressable>
```

React Native runs on React

## What is React Native?

We have React.js which is a JavaScript library for building UI for web development. Actually it's react-dom which adds the
web support. React by itself is platform-agnostic, it doesn not cares about underlying platform. React just gives one tools
to manage state for building virtual components then one needs react-dom which translates this React to platform dependent
stuff in case of web development.

In this way React Native is alternative to react-dom such that it will provide necessary components to build native app for
mobile platforms. So React Native comes with some special React components which then gets compiled to native UI elements.
React Native also provides APIs which exposes native device capabilities which one can then utilise to add device capabilities
related funtionalities.

So one can say

React + React Native = React Native Mobile Apps

|Web|Android|iOS|React Native JSX|
|---|---|---|---|
|<div>|android.View|UIView|<View>|
|<input>|EditText|UITextField|<TextInput>|

React Native will map and compile components to their platform equivalents. UI elements as mentioned above gets compiled
to native ones as per the targeted platform, however along with UI, there is also JavaScript code for logic. This JavaScript
code need not to be compiled, instead this code is run in a JavaScript thread hosted by React Native. React Native spins
up a process for running the JavaScript code.

|Expo CLI(Command Line Interface)|React Native CLI|
|---|---|
|Third Party Service|Provided by React Native team|
|Managed app development||
|Convenient||
|Can be left anytime to use React Native CLI|It's easy to integrate with native source code|

There is no CSS in React Native, so no CSS files are used. One provide style either using Inline styles or using StyleSheet
Objects. React Native uses props for styling which are inspired by CSS so sometimes naming might match.

CSS cascading styling where the child elements by default get styling coming from parent elements isn't replicated in React
Native.

## Flexbox

Flexbox stands for Flexible Box Layout is a layout model in CSS which aims at providing efficient way to lay out, align 
and distribute space among items in a container, even when their size is unknown and/or dynamic (thus the word “flex”).

In React every <View> by default organizes it's content via Flexbox. Also by default the organization by Flexbox in React
is in a column.
In contrast to web development, the Flexbox is NOT turned ON by default. With Flexbox turned ON in web the behaviour by
default is different in sense that it organizes child elements in row instead of column as in React Native.

In Flexbox main axis depends upon flex direction.
There are two axis in Flexbox :
- main axis
- cross axis

|flex direction|main axis|cross axis|
|---|---|---|
|row|left -> right|top -> bottom|
|row reverse|right -> left|bottom-top|
|column|top -> bottom|left -> right|
|column reverse|bottom -> top|right -> left|

justifyContent organizes content along -> main axis
alignItems organizes content along -> cross axis


Source : https://css-tricks.com/snippets/css/a-guide-to-flexbox/


## Handling Events

Handling events in React Native works same as it works in React using event listeners, handlers and hooks.
Usually when one makes components so that those could be re-used elsewhere in app as well and avoid code repitition, one
can pass props so as to pass data from the point where the create component will get used. There might be elements like
buttons as well in these components which need some event handlers. One can also pass event handler functions as part of
props as well.

## <ScrollView>

ScrollView will always render all the elements even if those are currently not being displayed on screen. This can become
a performance issue if one is showing a list of views running too large. One should use another component <FlatList> for
such case. <FlatList> will only render elements which are needed to show.