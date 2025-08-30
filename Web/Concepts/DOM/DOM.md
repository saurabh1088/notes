# DOM - Document Object Model


## What is DOM?
- DOM is Document Object Model
- It is a programming interface (an object representation) of a web page that browsers create when they load HTML.
- The DOM models a web page as a tree of objects (nodes), where each element, attribute, and piece of text is a node.

---

- The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content. The DOM models a web page as a hierarchical tree of objects, where each object, or node, represents a part of the document.

## DOM Tree Structure
- The tree begins with the Document node at the top. Everything else in the web page is a descendant of this node.
    - Element Nodes:
        - These nodes represent HTML tags, such as <html>, <head>, <body>, <h1>, and <p>.
        - They are the main building blocks of the tree.

    - Attribute Nodes:
        - These are properties of element nodes, like id or src.
        - They contain information about an element but are not elements themselves.

    - Text Nodes:
        - These nodes hold the text content within an element.
        - For example, the text "Welcome" inside an <h1> tag would be a text node.

- This tree-like structure defines the relationships between all parts of the document, such as parent, child, and sibling nodes, allowing developers to programmatically access and manipulate them.
