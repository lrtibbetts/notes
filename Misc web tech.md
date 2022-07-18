To investigate
- logging / telemetry


##### Compilers
- Babel: [[Source-to-source compiler]] that converts ES15+ JavaScript into older versions of JS
- swc (Speedy Web Compiler): Rust-based web platform. It can be used for compilation and bundling. Claims to be 20x faster than Babel. Used by tools like Next.js, Parcel, and Deno
- svelte: compiles to vanilla JS


##### Bundlers
- Webpack: module bundler for JS. It takes modules with dependencies and generates static assets representing those modules. Supports ES Modules and CommonJS
	- [Hot module replacement (HMR)](https://webpack.js.org/guides/hot-module-replacement/): allows modules to be updated at runtime without the need for a full refresh. Should only be used in development
- rollup.js: also a module bundler for JS. Uses ES Modules (not CommonJS). Doesn't handle node modules ([plugin](https://www.npmjs.com/package/@rollup/plugin-node-resolve)). Does not support HMR.
- Parcel: another bundler. "zero configuration".
	- Hot reloading
	- Written in Rust (built on swc)
	- Automatically handles JSX, [[TypeScript]]
- Browserify


##### Static type-checkers
- [[TypeScript]]
- Flow


##### Linting
- eslint
	- eslint-plugin-compat: check browser compatability
	- 


##### Build, publish, test
- lerna: build system for managing and publishing multiple JS/TypeScript packages from the same repository
- rush: monorepo manager for the web. Lets you build and publish many JS packages from a common Git repo.
- bazel: build and test


##### Deployment, hosting
- Vercel
- Render
- Netlify
- GitHub pages


##### Package managers
- Yarn (stands for Yet Another Resource Negotiator)
- npm


##### UI frameworks
- React
- Preact: lightweight alternative to React
- Vue


##### API frameworks
- FastAPI: for developing Python APIs
	- based on pydantic: provides data validation
- More Python frameworks: Django, Flask
- Express (JS)


##### [[Template Engines]]
- Pug (prev. Jade)
- Mustache


##### Content Management Systems (CMS)
- Drupal

