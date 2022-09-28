- CSS = Cascading Style Sheets
- stylesheet language used to describe the presentation of a document written in HTML or XML
- extensions
	- Sass (Syntactically Awesome Style Sheets). you can compile Sass files to CSS
	- 2 syntaxes: `.scss` is most commonly used. it's a superset of CSS, aka all valid CSS is also valid SCSS. `.sass` uses indentation rather than curly braces, and newlines instead of semicolons.
- CSS frameworks
	- [Tailwind](https://tailwindcss.com/)
- Centering things
	- text: `text-align`
	- can use `flex` and `justify-content`
- [Containing block](https://developer.mozilla.org/en-US/docs/Web/CSS/Containing_block)
- [`position`](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
	- `static`: element is positioned according to normal document flow. This is the default value
	- `relative`: positioned according to normal document flow and then offset *relative to itself*
	- `absolute`: element is removed from normal document flow. It is positioned relative to its closest positioned ancestor.
	- `fixed`: element is removed from normal document flow. It is positioned relative to the initial containing block established by the viewport
	- `sticky`: element is positioned according to the normal flow of the document, and then offset relative to its nearest scrolling ancestor and containing block


##### Resources
- https://blog.devgenius.io/css-display-flex-vs-block-inline-and-inline-block-explained-5fa588a3a960
	- Every HTML element has a default display behavior.
	- Elements like `<div>`, `<p>`, `<ul>` have default *block-level* display behavior
	- *Block-level* means the element will take the full width of a complete row
	- Elements like `<span>`, `<a>`,  `<button>` and `<img>` have default *inline* behavior.
	- `<div>` and `<span>` are much the same, except `<div>` is block-level and `<span>` is inline
	- Inline means the elements will be side by side
	- Width and height properties cannot be applied to inline elements
	- *Inline-block*
		- can apply width and height properties to elements
		- can place elements side by side
	- Flex property
		- larger CSS module with child properties
		- if a container is assigned `display: flex`, all elements will automatically be placed side by side. The container still takes the full width of the row and behaves like a block-level element
		- `inline-flex`: the container will take the necessary space as large as its children
	- https://web.dev/avoid-large-complex-layouts-and-layout-thrashing/
		- Avoid layout thrashing!
	- Interactive buttons https://www.codelord.net/2013/11/12/css-tip-stop-your-buttons-from-flickering/
	- https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Organizing

	