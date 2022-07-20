What is it?
1. a compiler
2. a server side HTTP handler
3. a server framework
4. a browser framework

##### Compiler
`remix build`
- built on esbuild
- generates:
	- a server HTTP handler, usually `server/build/index.js`
	- a browser build, usually in `public/build/*`
	- an asset manifest

##### HTTP handler
- remix is not actually a server. it is just a handler that is given to an actual JS server. it is built on the fetch API instead of [[Node.js]].
- Express is the actual server; Remix is just the handler
- `@remix-run/express`
is an adapter. handlers are server agnostic. adapters make them work for a specific server by converting the server's req/res API into the Fetch API on the way in, and adapting the Fetch response into the server's respoonse API.


##### Server Framework
- Remix provides the View and Controller of MVC, and leaves the Model up to you
- 