# DOM - Document Object Model

---

## What is DOM?
- DOM is Document Object Model
- It is a programming interface (an object representation) of a web page that browsers create when they load HTML.
- The DOM models a web page as a tree of objects (nodes), where each element, attribute, and piece of text is a node.


- The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content. The DOM models a web page as a hierarchical tree of objects, where each object, or node, represents a part of the document.

---

## DOM Tree Structure
- The tree begins with the Document node at the top. Everything else in the web page is a descendant of this node.
    - Element Nodes:
        - These nodes represent HTML tags, such as `<html>`, `<head>`, `<body>`, `<h1>`, and `<p>`.
        - They are the main building blocks of the tree.

    - Attribute Nodes:
        - These are properties of element nodes, like id or src.
        - They contain information about an element but are not elements themselves.

    - Text Nodes:
        - These nodes hold the text content within an element.
        - For example, the text "Welcome" inside an `<h1>` tag would be a text node.

- This tree-like structure defines the relationships between all parts of the document, such as parent, child, and sibling nodes, allowing developers to programmatically access and manipulate them.

---

## DOM, HTML, JavaScript - How these all come together to render page on web browser
- These can be thought of as three distinct but interconnected components of a web page.
- In a web page we have some content, the content is derived from a blueprint, then we have some way to add behaviour to
this content.
    - Content & Blueprint
        - This is the HTML which defines tags used to make a page
    - Behaviour
        - JavaScript is used to add behaviour. HTML is static, JavaScript adds dynamic behavior and interactivity to it.
- Now DOM is the interface and memory which connects HTML and JavaScript.

### What DOM does?
- When a browser loads an HTML page, it creates a tree-like representation of that page in memory
    - this is the DOM.
- Each HTML element, attribute, and piece of text becomes a node in this tree.
- JavaScript then uses the DOM as an API to access and manipulate the HTML structure and content.
- The DOM allows JavaScript to find, add, remove, and change the nodes of the HTML page.
- It's the blueprint that the construction crew (the browser) creates, allowing the smart home system (JavaScript) to understand and interact with every part of the house.

### How They Work Together?
1. HTML Loading:
    - The web browser first reads the HTML file. This file contains the initial structure and content of the page.
2. DOM Creation:
    - As the browser parses the HTML, it builds a DOM tree in the computer's memory. This tree is a live, dynamic representation of the HTML document.
3. JavaScript Execution:
    - The browser then executes the JavaScript code. This code can now access the DOM tree. Using methods like document.getElementById(), JavaScript can locate specific nodes (elements) within the tree.
4. Interaction and Updates:
    - When a user interacts with the page (e.g., clicks a button), the JavaScript code listens for that event. It then uses the DOM to modify the page. For example, JavaScript can remove a paragraph, change the text of a heading, or add a new image to the DOM tree. The browser then re-renders the page to reflect these changes.

In short, HTML provides the initial content, the browser uses it to create the DOM in memory, and JavaScript uses the DOM to manipulate that content and make the page interactive.

---

## Key points about DOM
- It’s not HTML itself, but a live representation of it.
- It allows JavaScript to interact with the page.
- It’s tree-structured (parent → child elements).
- Browsers constantly re-render when the DOM is updated.

