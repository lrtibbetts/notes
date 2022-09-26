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
is an adapter. handlers are server agnostic. adapters make them work for a specific server by converting the server's req/res API into the Fetch API on the way in, and adapting the Fetch response into the server's response API.


##### Server Framework
- Remix provides the View and Controller of MVC, and leaves the Model up to you
- Remix Route modules take on View and Controller responsibilities. Routes can contain both the UI and the interactions with the models in the same file (nice co-location)


##### Guides
- [Data Writes](https://remix.run/docs/en/v1/guides/data-writes#html-form-post)
	- built on top of `<form>` API
	- big forms and buttons alike can be handled with a form post
- Form stuff: clearing input, changing focus after submit. https://www.youtube.com/watch?v=bMLej7bg5Zo
- 


#web