Document Object Model (DOM)

[Intro](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- object-oriented representation of a web page
- implementations of the DOM can be built for any language
- `Document` interface
	- represents any web page loaded in the browser and serves as an entry point into the web page's content (the DOM tree)
	- HTML documents also implement `HTMLDocument`, XML and SVG documents implement `XMLDocument`
- `Window` interface
	- represents a window containing a DOM document
	- `document` property points to the document loaded in the window
	- window for a given document can be obtained with `document.defaultView` property
	- a global variable, `window`, representing the window in which the script is running, is exposed to JS code
- `Node`: every object within a document is a node of some kind
- `Element`: refers to a node of type `element`. Elements in HTML docs also implement `HTMLElement`, and potentially more specific interfaces like `HTMLTableElement`
- `NodeList`: array of elements, e.g. return type of `document.querySelectorAll()`.
- 