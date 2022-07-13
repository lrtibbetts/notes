- Use `let` to declare immutable constants, `var` to declare mutable variables
- A `protocol` defines a set of methods, properties, and other requirements for a given task or piece of functionality
- Types are either *value types* (structures, enumerations, tuples) or *reference types* (classes)
	- instances of value types keep unique copies of data
	- instances of reference types share a single copy of data
- `open` versus `public`
	- [proposal](https://github.com/apple/swift-evolution/blob/master/proposals/0117-non-public-subclassable-by-default.md) for the addition of `open` to Swift
	- an `open` class is accessible and subclassable outside of the defining module. `open` class members are accessible and overridable outside of the defining module
	- a `public` class is accessible but **not** subclassable outside of the defining module, `public` class members are accessible but **not** overridable outside of the defining module
- Declarations in Swift default to `internal` access control, encouraging code authors to think more carefully about publicly exposed interfaces
- `==` checks if instance values are equal, `===` checks reference equality

- Can execute `xcrun swift` to access Swift [[REPL]]


#pl