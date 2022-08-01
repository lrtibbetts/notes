Goal of TypeScript: static typechecker for [[JavaScript]] programs

#### [TypeScript for OOP programmers](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes-oop.html)
- C# and Java are *mandatory OOP languages*, aka the class is the basic container of all data *and* behavior at runtime
- In JavaScript, functions can live anywhere, and data can be passed around without being inside a class or struct
- C# and Java have *nominal, reified type systems*: types are related via declarations, not structures, and types are present at runtime
- TypeScript's type system is *structural*, not nominal. It also is not reified: there is no way to know at runtime that an object satisfies a particular interface or not. The type system is fully erased.

#### [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/2/basic-types.html)

##### The Basics
- ``tsc`` is the TypeScript compiler. Can execute ``tsc hello.ts`` to compile TypeScript file into JS file
- TypeScript will still compile to JS in the presence of type-checking errors. Can use ``tsc --noEmitOnError hello.ts`` to change this behavior
- Note: ``Date()`` returns a string, whereas ``new Date()`` returns a Date object
- In many cases, TypeScript can infer types. It's best not to add annotations when the type system would end up inferring the same type anyway
- Template strings, are a feature of ECMAScript 2015 (ES6). TypeScript can rewrite code from newer versions of ECMAScript to older ones (*downleveling*), and by default targets ES3. Can run ``--target es2015``. Great majority of current browsers support ES2015.
- TypeScript provides strictness settings. The ``strict`` flag in the CLI, or ``"strict": true"`` in a ``tsconfig.json`` toggles them all on simultaneously. Important flags:
	- ``noImplicitAny``: will issue an error an any variables whose type is implicitly inferred as ``any``
	- ``strictNullChecks``: makes handling ``null`` and ``undefined`` more explicit

##### Types
- Three commonly used primitives: ``string``, ``number``, and ``boolean``
- The syntax for specifying the type of an array is ``number[]`` or ``Array<number>``
- Type annotations on variables are optional, e.g. ```
```
	let myName: string = "Lucy";
```
- TypeScript lets you specify the types of both input and values of functions
- Arow functions were introduced with ES6, e.g. 
```
(s) => { 
  console.log(s.toUpperCase());
}
```
- *Contextual typing:* when TypeScript uses the context a function occurs within to inform what type it should have
- *Anonymous function*: (also: lambda function/expression) a function definition not bound to an identifier. Often, arguments being passed to a higher-order function
- Object ex:
```
function printCoord(pt: {x: number; y: number}) { // ; or , can be used to separate
  console.log(`x: ${pt.x}, y: ${pt.y}`);
}
```
- Optional properties specified with ``?``
- If you access a property that doesn't exist, you will get the value ``undefined`` rather than a runtime error. When reading from an optional property, you need to check for ``undefined`` before using it.
- Type alias ex:
```
type Point = {
  x: number;
  y: number;
}

function printCoord(pt: Point) {
  console.log(`x: ${pt.x}, y: ${pt.y}`);
}
```
- You can use type aliases with any type, not just objects, e.g.
```
type ID = number | string;
```
- Interface declarations are another way to name object types, e.g.
```
interface Point {
  x: number;
  y: number;
}
```
- Type aliases vs. Interfaces
	- You can use `extends` to extend an interface. You can use intersections (`&`) to extend a type (combine multiple types)
	- You can add new fields to an existing interface. You *cannot* add new fields to a type
	- Interfaces can only be used to declare the shapes of objects, not to rename primitives
- You can use *type assertions* to specify more specific types (using ``as``)
- You can combine literals into unions to do things like defining a function that only accepts a certain set of known values, e.g.
```
function print(s: string, alignment: "left" | "right" | "center") {
  ...
}
```
- Two primitive values to signal absent/uninitialized value: ``null`` and ``undefined``
- Writing ``!`` after an expression acts as a type assertion that the value isn't ``null`` or ``undefined``, e.g.
```
function liveDangerously(x?: number | null) {
  console.log(x!.toFixed());
}
```
You should only do this when you know a value *can't* be ``null`` or ``undefined``
- Enums are a TypeScript addition to JS at the language/runtime level. Use with caution

##### Narrowing
- Process of refining types to more specific types than declared is called *narrowing*
- Checks like ``typeof padding === "number"`` are called *type guards*
- Note: arrays are object types in JS (``typeof someArray === "object"``)
- Also note: (``typeof null === "object"``)
- In JS, any expression can be used in conditionals. Expressions are "coerced" to ``booleans`` so they can be parsed
- You can coerce values to ``booleans`` using the ``Boolean`` function, or double-Boolean negation, e.g.
```
Boolean("hello"); // type: boolean, value: true
!!"world"; // type: true, value: true
```
- A non-boolean value that counts as ``true`` is "truthy"
- ``===`` compares type and value. ``==`` does any necessary type conversion before comparing value. It is much better to use ``===``.
- There is a distinction between observed type and declared type. Assignability is always checked against declared type. E.g.
```
let x = Math.random() < 0.5 ? 10 : "hello"; // let x : string | number (declared type)
x = 1 // let x: number (observed type)
x = true; // ERROR: Type 'boolean' is not assignable to type 'string | number'.
```
- Type predicate example:
```
function isFish(pet: Fish | Bird): pet is Fish {
  return (pet as Fish).swim !== undefined;
}
```
- Discriminated unions: when every type in a union contains a common property of a literal type (known as a *discriminant property*), TypeScript considers it to be a *discriminated union*, and can narrow out the members of the union

##### Functions
- You can use *call signatures* to specify properties of a function, e.g.
```
  type describableFxn = {
    description: string;
    (someArg: number): boolean;
  }
```
- You can also define *construct signatures*, e.g.
```
type someConstructor = {
  new (s: string): someObject;
};

function fn(ctor: someConstructor) {
  return new ctor("hello")
}
```
- Call and construct signatures can be combined arbitrarily in the same type
- *Generics* syntax in JS ex:
```
function firstElement<Type>(arr: Type[]): Type | undefined {
  return arr[0];
}
```
- You can also *constrain* type parameters, e.g.
```
function longest<Type extends { length: number }>(a: Type, b: Type) {
 ...
}
```
- Type parameters are for *relating the types of multiple values*. If a type parameter is only used once in a fxn signature, it's not relating anything
- The JS fxn ``toFixed()`` converts a number to fixed-point notation and returns its value as a string
- You can provide parameter defaults, e.g.
```
function f(x = 10) {
  ...
}
```
-  To overload a function in JS, you can write some number of function signatures followed by the body of the function. Note: the signature used to write the function body (the *implementation signature* can't be "seen" from the outside.
- Note: always prefer parameters with union types instead of overloads
- Other types to know about (esp. relevant for fxns)
	- ``void``: return value of fxns that don't return a value. NOT the same as ``undefined`` in TypeScript
	- ``object``: refers to any value that isn't a primitive
	- ``unknown``: represents any value. safer than ``any`` because it isn't legal to do anything with an ``unknown`` value
	- ``never``: can be used to indicate a fxn doesn't return a value (e.g. throws an exception)
	- ``Function``: global type that describes properties like ``bind``, ``call``, ``apply``. Values of type ``Function`` can always be called (and return ``any``). The type ``() => void`` is generally safer
- Note: function values are objects
- Rest parameters: use the ``...`` spread syntax to indicate an unbounded # of arguments
- Rest arguments: use spread syntax to *provide* a # of arguments from an array, e.g.
```
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
arr1.push(...arr2);
```
- Note: A return type of ``void`` does NOT force functions to NOT return something, i.e. functions with a void return type can return *any* other value, but it will be ignored

##### Object Types
- Fundamental way to group and pass around data in JavaScript is through *objects*. We represent objects in TypeScript through *object types*. Objects can be anonymous, or named using either an interface or a type alias.
- You can use *mapping modifiers* to remove attributes from objects. Specifically: `readonly` or `optional`.
- You can use *index signatures* to describe the types of possible values, e.g.
	```
	interface StringArray {
	  [index: number]: string;
	}
	```
	This index signature indicates that when a `StringArray` is indexed with a `number`, it will return a `string`. 
- Polymorphism is achieved in TypeScript with the `extends` keyword
- Typescript also provides a construct called *intersection types* that can be used to combine existing object types.
- Object types with generics ex:
```
interface Box<Type> {
  contents: Type;
}

let box: Box<string>;
```
- Type aliases can also be written using generics, and can be used to describe more than object types, e.g.
```
type OrNull<Type> = Type | null;
```
- Arrays are an example of generic types. That is, `string[]` is shorthand for `Array<string>`. TypeScript also provides the type `ReadonlyArray`. Note: unlike the `readonly` property modifier, assignment is *not* bidirectional between regular `Array`s and `ReadonlyArray`s.
- Tuple type ex:
```
type StringNumberPair = [string, number];
```
- Tuple types are useful in APIs where each element's meaning is "obvious." This often is not the case, so it is worth considering using object types with descriptive property names.
- Tuples can have rest elements of variable length, e.g.
```
type StringNumberBooleans = [string, number, ...boolean[]]
```
- Note: array literals with `const` assertions will be inferred as `readonly` tuples, e.g.
```
let point = [3, 4] as const;
```

##### Type Manipulation
- We can use interfaces to add constraints to the types accepted by a generic function
- The `keyof` operator takes an object type and produces a string or literal numeric union of its keys.
- Note: in JavaScript, object keys are always coerced to a string, i.e. `obj[0]` is the same as `obj["0"]`
- We can use *indexed access types* to look up specific properties on other types, e.g.
```
type Person = { age: number; name: string }
type Age = Person["age"];
```
- You can use `number` to get the type of an array's elements
- *Conditional types* ex:
```
SomeType extends OtherType ? TrueType : FalseType;
```
- Conditional type constraint ex:
```
type MessageOf<T> = T extends { message: unknown } ? T["message"] : never;
```
- Inferring with conditional types using `infer` keyword ex:
```
type Flatten<Type> = Type extends Array<infer Item> ? Item : Type;
```
- A *mapped type* is a generic type which uses a union of `PropertyKey`s (frequently created via `keyof`) to iterate through keys and create a type, e.g.
```
type OptionsFlags<Type> = {
  [Property in keyof Type] : boolean;
}

type FeatureFlags = {
  darkMode: () => void;
  newUserProfile: () => void;
}

type FeatureOptions = OptionsFlags<FeatureFlags>;
```
- *Template literal types* ex:
```
type World = "world";
type Greeting = `hello ${World}`; // type Greeting = "hello world"
```
- TypeScript includes intrinsic string manipulation types
	- `Uppercase`
	- `Lowercase` 
	- `Capitalize`
	- `Uncapitalize`






##### Classes
- The `class` keyword was introduced in ES2015. Ex.
```
class Point {
  x: number;
  y: number;
}
```
- `--strictPropertyInitialization` controls whether class fields need to be initialized in the constructor
	- Note: fields need to be initialized *in the constructor itself*. TypeScript does not analyze mthods invoked from the constructor, because a derived class might override those methods and fail to initialize.
	- You can use the *definite assignment assertion* operator: `!`
- Same as in JS, if you have a base class, you'll need to call `super();` in your constructor body before using any `this.` members.
- Note: inside a method body, it is mandatory to access fields and other methods via `this.`. An unqualified name in a method body will refer to something in the enclosing scope.
- Note: getters/setters without extra logic are rarely useful in JS. It's fine to expose public fields
- You can use `implements` to specify that a class satisfies an interface
- You can use `extends` to create a derived class (has all the properties and methods of its base class, and can define additional members)
- Note: when `target >= 2022` or `useDefineForClassFields` is `true`, class fields are initialized after the parent class constructor completes, overwriting any value set by the parent class. You can write `declare` to indicate to TypeScript that there should be no runtime effect for a field declaration.
- Default visibility of class members is `public`
- Note: `private` and `protected` are only enforced during type checking, i.e. JavaScript runtime constructs like `in` or simple property lookup can still access `private` or `protected` members
- Note: `private` also allows access using bracket notation during type checking. "Soft private"
- JS's private fields (`#`) remain prviate after compilation. "Hard private"
- TypeScript and JS don't have static classes. Why? A class with only a single instance is typically just represented as a normal *object*
- You can have `static` blocks in classes
- Note: the `static` members of a generic class can never refer to the class's type parameters
- JS does weird things with `this`. The value of `this` inside a function depends on how the function was called.
	- TypeScript checks that calling a function with a `this` parameter is done so with a correct context.
- TypeScript offers special syntax for turning constructor params into class properties (*parameter properties*)
- You can also write *class expressions*
- Classes in TypeScript are compared structurally, same as other types.




##### Modules
-  JS has converged on a format called ES (or ES6) Modules, aka `import/export` syntax.
- Any file containing a top-level `import` or `export` is considered a module. Files without `import/export` are considered scripts, not modules. Variables and types in script files are in the shared global scope.
- Types can be exported and imported using the same syntax as JavaScript values
- Precursor to ES Modules = CommonJS, uses `require` keyword. Ex:
```
module.exports = {
  pi: 3.14
}

// separate file
const maths = require("maths");
maths.pi;
```
- Compiler flag to reduce friction between ES Modules and CommonJS: `esModuleInterop`
- There are many TSConfig flags that influence module strategy



##### Declaration files
- predefined modules that describe the shape of JS values, or the types present, for the TS compiler
- usually contained in files with a `.d.ts` extension
- can be installed via npm using `@types`


##### APIs of interest
- `Pick`
- `Awaited`
- `ReturnType`

#pl #web