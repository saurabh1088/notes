#  ReactNative

React Native is an open-source Framework which was developed by FaceBook. React Native enables one to build mobile 
applications using JavaScript and React. Aim here is to create cross-platform applications which can run both on iOS and 
Android platforms sharing a huge chunk of codebase.

Code is written in JavaScript and further rendered with native code.

React Native provides native components which map directly to target platform's native ones.

Similar to concept of views in iOS and Android, React Native also has views as the basic building blocks of user interface.
Everything seen on the UI boils down to a view.

React Native comes with some *Core Components* which are ready to use components for builiding UI. One can also build custom
native components.

React Native UI Components

<View>
<Text>
<Image>
<ScrollView>
<TextInput>

React Native runs on React

What is React Native?

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

## Flexbox

Flexbox stands for Flexible Box Layout is a layout model in CSS which aims at providing efficient way to lay out, align 
and distribute space among items in a container, even when their size is unknown and/or dynamic (thus the word “flex”).

Source : https://css-tricks.com/snippets/css/a-guide-to-flexbox/
