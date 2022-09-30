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
- `rem` = root element's font size


#### Resources
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
	- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Aligning_Items_in_a_Flex_Container
		- (!) If `flex-direction` = column, `align-items` will align items horizontally


#### CSS Building Blocks

##### Cascade and inheritance
 https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance
- Stylesheets *cascade*, aka the order of CSS rules matter. When 2 rules from the same cascade layer apply and both have equal specificity, the one defined last in the stylesheet will be used
- Specificity
	- element selector = less specific, e.g. `h1`
	- class selector = more specific
- Inheritance
	- some properties are inherited; some are not
	- e.g. `color` and `font-family` are inherited (unless overridden by child values)
	- e.g. `width` is not inherited
- Controlling inheritance
	- `inherit`: "turn on inheritance"
	- `initial`: initial value = default value of a CSS property
- Three factors influence what properties are applied (listed in increasing precedence):
	- Source order
	- Specificity
	- Importance
		- `!important` flag. Don't use it unless you have to
- *Note*: inline styles **always** take precedence over stylesheets

##### Selectors
https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors
Types of selectors:
- element, class, id (specified with `#`)
- attribute e.g. `a[title]`
- pseudo-classes/elements: style certain states e.g. `a:hover`, `p:first-line`
- combinators. e.g. `article > p`  selects paragraphs that are direct children of `<article>` elements


##### The Box Model
- 2 types of boxes: block and inline
- boxes have an *inner display type* and *outer display type*
- inner display type dictates how elements inside a box are laid out
	- you can change inner display type e.g. `display: flex`. the element will still use the outer display type `block` but the inner display type will be `flex`
- parts of a box
	- content box
	- padding box: sits around the content
	- border box: wraps the content and any padding
	- margin box: outermost layer
	  ![[Pasted image 20220928103138.png]]  
- alternative box model: any width = width of the visible box. content area width = that width minus the width for the padding and border. can turn on with `box-sizing: border-box`
- margin
	- pushes other elements away from the box
	- setting a negative margin can cause overlapping
	- more on [margin collapsing](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)

##### Additional notes
- When you use margin and padding set in percentages, the value is calculated from the inline size of the containing block (aka width when working in a horizontal language)
- viewport = visible area of your page in the browser. `vw` = viewport width, `vh` = viewport height
- BEM = block, element, modifier. naming convention for CSS classes