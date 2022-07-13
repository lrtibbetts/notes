Good [overview](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/)

Q's to dig into:
- How does method overload resolution work?

##### How is C sharp compiled and executed?
- C# runs on .NET, which consists of a common language runtime (CLR) and class libraries. The CLR is Microsoft's implementation of the common language infrastructure (CLI) standard, defined in ECMA-335
- There are different implementations of CLR: the .NET Framework, .NET Core, Mono (open-source)
- C# is [[Managed code]]. It compiles into Common Intermediate Language (CIL), an [[Intermediate representation]] defined within the CLI spec. CIL code and resources live in an assembly, typically .dll (dynamic link library) files
- When a C# program is executed, the assembly is loaded into the CLR. The CLR performs [[JIT compilation ]].

#pl

