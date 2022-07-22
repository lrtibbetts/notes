- a rendering option defines the stage at which your page's user-facing HTML is generated
- it can be at build time (SSG or pre-rendering), during HTTP request (server-side rendering) or locally in the browser with JS (client-side rendering)
- **Static Site Generation (SSG)**: the entire site is pre-rendered into HTML, CSS, and JS at build time, which then get served as static assets to the browser. SSG serves websites in the **fastest possible way**. One downside is longer build times
	- Deferred SSG: only difference from SSG is that developers can defer building certain pages until the first time a user requests it
	- static renders can be deployed to multiple [[Content Delivery Network (CDN)]]s to take advantage of edge-caching
	- individual HTML files must be generated for every possible URL. this can be challenging or infeasible
	- to combat long build times, Next.js provides Incremental Static Regeneration (ISR)
- **Pre-rendering**: running a client-side application at build time to capture its initial state as static HTML
- **Server-side rendering (SSR)**: each web page is served to a site visitor at runtime, i.e. a portion of the build process happens on each page request.
	- visitors will always get the latest content from the server, but may have to wait a few seconds for it to display
	- avoids additional round-trips for data fetching and templating
- **Hydration (or rehydration)**: client-side JS converts a static HTML web page (delivered via SSG or SSR) into a dynamic web page by attaching event handlers to the HTML elements
- **Client-side rendering (CSR)**: rendering pages directly in the browser with JS
	- can be difficult to get and keep fast for mobile
	- primary downside = amount of JS the browser needs to run as an application grows
	- Code-splitting and lazy-loading can be used to reduce JS payloads
- **Streaming server rendering** allows you to send HTML chunks that the browser can progressively render
- Metrics to consider
	- TTFB = time to first byte
	- TTFP = time to first paint
	- FCP = first contentful paint
	- LCP: largest contenful paint
	- TTI = time to interactive
	- CLS = cumulative layout shift


##### [When To Fetch](https://www.youtube.com/watch?v=95B8mnhzoCM)
- you need to intiate fetching *before* rendering
- decouple:
	- initiating fetches
	- reading results
	- rendering fallbacks
- why doesn't react 18 solve this?
	- RSC (React Server Components): moves rendering and data fetching to the server
	- Streaming: sends the document in chunks during initial SSR
	- Suspense: defines where the UI can fallback when components are reading data
		- not designed to define where you *initiate* fetches, but rather *where you access the results*
- react router / remix lets you initiate fetches for all the components on a page  
 *in parallel*
- goal is always: parallelize, unblock
- inherent tradeoff between: TTFB and LCP. E.g. fetching data from the server speeds up LCP but slows down TTFB
	- caching can help here
	- the lever for this tradeoff in remix is just `await`

Resources
- https://web.dev/rendering-on-the-web/
- https://www.gatsbyjs.com/docs/conceptual/rendering-options/
- https://www.joshwcomeau.com/react/the-perils-of-rehydration/

#web