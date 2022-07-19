React is:
- declarative
- component-based

[Modern JS refresher](https://gist.github.com/gaearon/683e676101005de0add59e8bb345340c)
- the value of `this` in a method depends on how it is called
- arrow functions don't have their own `this` value, so they are handy when you want to preserve an outer method's definition of `this`

##### [[JSX]]
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

##### State and lifecycle
- the `render()` method in a class component will be called each time an update happens, but as long as the component is rendered into the same DOM node, a single instance of the class will be used.
- class components should always call the base constructor with `props`
- "mounting" = a component is rendered to the DOM for the first time
- "unmounting" = component is removed from the DOM
- lifecycle methods: `componentDidMount()`, `componentWillUnmount()`
- we can use `this.setState()` to update local component state
- important notes about using state:
	- do not modify state directly (i.e. `this.state.comment = 'hello'`. instead use `setState()`
	- `this.props` and `this.state` may be updated asynchronously. you should not rely on their values for calculating the next state
	- state updates are merged into the current state
- state is not accessible to any component other than the one that owns and sets it. state can be passed down as props to a child component

##### Events
- you must call `preventDefault` explicitly in React
- [W3C spec](https://www.w3.org/TR/DOM-Level-3-Events/) for synthetic events. The React implementation is `SyntheticEvent`. It is a cross-browser wrapper around the browser's native event. You can access the underlying browser event with `nativeEvent` property.
- in JS, class methods are *not* bound by default.
```
// This binding is necessary to make `this` work in the callback    
this.handleClick = this.handleClick.bind(this);  }
```
- you can pass additional arguments to event handlers, e.g.
  ```
  onClick={(e) => this.deleteRow(id, e)}
  ```

##### Conditional Rendering
- you can use `if` to conditionally render components
- you can also use JSX and `&&` to provide an inline `if`, e.g.
```
{someCondition && <h2>conditionally rendered text</h2>}
```
- another inline option is using `condition ? true : false`
- you can return `null` from `render()` to have a component hide itself. note that returning `null` does not affect the firing of lifecycle methods, e.g. `componentDidUpdate` will still be called

##### Lists and Keys
- you need to provide a "key" when creating lists of elements. keys help React identify which items have changed, are added, or are removed. the best candidate here is a stable id for each item
- keys need to be unique among their siblings. they don't need to be globally unique

##### Forms
- an input form element whose value is controlled by React is called a *controlled component*
- you can use the same approach (React as source of truth) for things like text areas, `<select>`, etc.
- specifying the `value` prop on a controlled component prevents the user from changing the user unless you desire so
- [Formik](https://formik.org/) is a popular library for handling forms


##### Lifting state up
- when several components need to reflect the same changing data, it is recommended to lift the shared state up to the closest common ancestor
- props are read-only, so a child component cannot directly modify shared state passed as props. instead it can accept a callback as props, e.g. `onTemperatureChange`()
- there should be a single "source of truth" for any data that changes in a React application
- you should rely on top-down data flow


##### Composition vs inheritance
- it is recommended to use composition instead of inheritance as a means of reuse
- some components don't know their children ahead of time. such components can use the special `children` prop to pass children elements directly into their output
- sometimes components are "special cases" of other components. this can be achieved by composition, where a more "specific" component renders a more "generic" one and configures it with props


##### Thinking in React
- start with a mock
- step 1: break the UI into a component hierarchy
- step 2: build a static version
- step 3: identify the minimal (but complete) representation of UI state
- step 4: identify where your state should live
- step 5: add inverse data flow

#web