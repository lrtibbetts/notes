- Lightweight, interpreted, object-oriented language
- Implementation of ECMAScript, an open standard


- The [prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
	- JS only has one construct: objects. Each object has a private property which holds a link to another object called its *prototype*
	- The prototype chain ends when an object is reached with `null` as its prototype
	- It is possible to mutate any member of the prototype chain (or swap out prototypes) at runtime (!)
	- `__proto__` is the accessor for an object's prototype
- `var` versus `let` versus `const`
	- `var` variables declared outside of a function are globally scoped. `var` variables declared inside a function are function scoped. var` variables can be re-declared
	- `let` is preferred over `var` for variable declaration. `let` is block scoped. `let` variables can be updated but not re-declared.
	- `const` variables maintain constant values. They are block scoped, and cannot be updated *or* re-declared.
- *Hoisting* refers to the process whereby the interpreter appears to move teh *declaration* of functions, variables, or classes to the top of their scope, prior to execution of the code. Hoisting means you can safely use functions in code before they are declared.


#pl