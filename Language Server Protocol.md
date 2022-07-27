- Language Server Protocol (LSP) defines the protocol used between an editor/IDE and a language server that provides features like auto-complete, go to definition, find all references, etc.
- LSIF = Language Server Index Format
	- standard format for language servers to emit their knowledge about a code workspace. the persisted information can later be used to answer LSP requests without running a language server
	- with LSIF, a build step in CI can dump information about the code to a portable file. code browsers can use that LSIF dump to provide hover tooltips, jump-to-definition, find-references, etc.


##### Resources
- https://microsoft.github.io/language-server-protocol/