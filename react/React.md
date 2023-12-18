#  React

react-dom for web apps and react-native for native mobile apps

React lets one build user interfaces out of individual components. One can also
create their own components and then use those to create screens, views, apps.



## Components

A React app is made from *components*. A *Component* is something which has its
own logic and appearance, it can be a very small and simple like a button, or can
be more complex like a full page.

React components are basically JavaScript functions. These functions are expected
to return a markup.

Once a component is declared, it can be used and nested in other components.

React component names must always start with a capital letter, while HTML tags 
must be lowercase. 

CSS class is specified with *className*, which works the same way as the HTML 
*class* attribute.

```
<img className="cssClassName" />

/* In CSS File */
.cssClassName {
  border-radius: 50%;
}
```

## JSX

JSX is a syntax extension for JavaScript. JSX lets one write HTML like markup inside
a JavaScript file.

Web is built using :
- HTML
- CSS
- JavaScript
with page content is written in HTML files, design is in separate CSS files and
the logic is encapsulated in JavaScript files.

In React however the rendering logic and markup can live together in same place.

JSX may look a lot like HTML but the syntax is stricter.

JSX and React are two separate things which are used together often, however one
can use these independent of each other.

|JSX|React|
|---|---|
|Is a syntax extension|Is a JavaScript library|

## Markup : Displaying data


