##### It's time to learn C

Resources
- K&R

"it wears well as one's experience with it grows"

##### Introduction
- pointers provide for machine-independent address arithmetic
- a preprocessing step performs macro substitution on program text, inclusion of other source files, and conditional compilation
- there are no operations to deal directly with composite objects, e.g. strings, sets, lists, arrays
- no heap or garbage collection
- C itself provides no input/output facilities (most C implementations have included a collection of such functions)
- only single-thread control flow
- biggest change to C introduced with ANSI standard = new syntax for declaring and defining functions. functions can now include a description of the function arguments
- not strongly-typed


##### Ch. 1: a tutorial introduction
- `#include<stdio.h>` tells the compiler to include information about the standard input/output library
- sizes of basic data types (like `int` or `float`) are machine-dependent
- can use `#define` to define a *symbolic name* or *symbolic constant*
- `EOF` = end of file. integer defined in `<stdio.h>``
- a character written between single quotes represents an integer value equal to the numerical value of the character in the machine's character set (*character constant*)
	- e.g. `'A'` is a character constant. in the ASCII character set its value is 65
- all function arguments are passed *by value* (pointers are used to pass arguments by reference)
- `int` is the default return type
- other functions cannot directly access private/local variables declared in `main()`. this is true for variables in other functions. each local variable comes into existence only when the function is called, and disappears when the function is exited. these variables are usually known as *automatic* variables
- external variables must be defined exactly once outside of any function. the variable must also be declared in each function that wants to access it (optionally with an explicit `extern` statement, or implicit from context)
	- it is common practice to place definitions of all external variables at the beginning of a source file and then omit the `extern` declarations
	- for multi-file programs, it is common to collect `extern` declarations in a separate (header) file
- Note: "definition" refers to the place wehre a variable is created or assigned storage. "declaration" refers to places where the nature of the variable is stated but no storage is allocated






