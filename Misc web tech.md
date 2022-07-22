To investigate
- logging, telemetry
	- google analytics
- [harp](http://harpjs.com/) (static web server)
- bootstrap (frontend framework)
- next.js
- remix


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
- [esbuild](https://esbuild.github.io/)


##### Static type-checkers
- [[TypeScript]]
- Flow


##### Linting
- eslint
	- eslint-plugin-compat: check browser compatability
	- 


##### Build, publish, test
- lerna: build system for managing and publishing multiple JS/TypeScript packages from the same repository
- Nx: build system with monorepo support
- rush: monorepo manager for the web. Lets you build and publish many JS packages from a common Git repo.
- bazel: build and test
- Earthly: run CI/CD pipelines anywhere


##### Deployment, hosting
- Vercel
- Render
- Netlify
- GitHub pages
- Heroku
- fly.io
- Cloudflare


##### Package managers
- Yarn (stands for Yet Another Resource Negotiator)
- npm


##### Frontend frameworks
- React
- Preact: lightweight alternative to React
- Vue


##### Web server frameworks
- Python: FastAPI, Django, Flask
- JS: Express, Koa, Fastify

#web


