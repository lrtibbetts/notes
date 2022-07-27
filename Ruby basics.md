- IRB = Interactive Ruby
- `puts` = print command
- to define a method (plus string interpolation):
```
def hi(name)
	puts "hello #{name}"
end
```
- use `@` to define instance variables in classes, e.g.
```
class Greeter
	def initialize(name = "World")
		@name = name
	end

	def say_hi
		puts "hello #{name}"
	end
end
```
- instance variables are available to all methods in a class
- to create an object
```
Greeter.new("Lucy")
```
- to provide access to a class's variable: `attr_accessor :var_name`. adds two methods: `var_name` to get the value and `var_name=` to set it.
- 


##### Ruby ecosystem
- default Ruby VM = YARV (yet another Ruby VM). written in C
- Ruby MRI (or CRuby) was the initial reference implementation of Ruby, written in C. starting with Ruby 1.9, YARV replaced MRI as the official interpreter
- [Sorbet](https://sorbet.org/) = static type checker for Ruby, built at Stripe. Stripe has also open-sourced an [ahead-of-time compiler](https://sorbet.org/blog/2021/07/30/open-sourcing-sorbet-compiler) for Ruby
	- the compiler process: `.rb` files are fed to Sorbet to be typechecked. the output is a custom type-annotated [[Intermediate representation]], which the Sorbet Compiler consumes to generate [[LLVM]] IR. LLVM takes this IR and generates native shared object `.so` files (which are also valid Ruby native extensions)
	- tl;dr: the sorbet compiler turns Ruby into a language for writing Ruby native extensions. you can write Ruby but gain the benefits of native compiled speeds
- JRuby = implementation of Ruby built atop the JVM
- [TruffleRuby](https://github.com/oracle/truffleruby) = GraalVM implementation of Ruby.


#pl
