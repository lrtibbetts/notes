React is:
- declarative
- component-based

[Modern JS refresher](https://gist.github.com/gaearon/683e676101005de0add59e8bb345340c)
- the value of `this` in a method depends on how it is called
- arrow functions don't have their own `this` value, so they are handy when you want to preserve an outer method's definition of `this`

##### JSX
Example:
```
const element = <h1>Hello, world!</h1>;
```
- syntax extension to JavaScript
- JSX produces React elements
- you can put any valid JS expression inside `{}` in JSX
- after compilation, JSX expressions become regular JS function calls and evaluate to JS objects
- JSX gets compiled into `React.createElement()` calls (you can use Babel, or the [TypeScript compiler](https://www.typescriptlang.org/docs/handbook/jsx.html#:~:text=JSX%20rose%20to%20popularity%20with,compiling%20JSX%20directly%20to%20JavaScript.))

##### Elements
- unlike DOM elements, React elements are plain objects, and cheap to create. React DOM takes care of updating the DOM to match the React elements
- React elements are *immutable*. The only way to update the UI is to create a new element.
- React DOM only updates when necessary

##### Components and props
- components are independent, reusable pieces
- conceptually, they are like JS functions. They accept arbitrary inputs (*props*) and return React elements
- the simplest component is a JS function. called a "function component"
- note: always start component names with a capital letter
- props are read-only. **all components must act like pure functions with respect to their props**
- 


