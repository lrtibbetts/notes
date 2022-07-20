- a rendering option defines the stage at which your page's user-facing HTML is generated
- it can be at build time (SSG or pre-rendering), during HTTP request (server-side rendering) or locally in the browser with JS (client-side rendering)
- SSG: the entire site is pre-rendered into HTML, CSS, and JS at build time, which then get served as static assets to the browser. SSG serves websites in the **fastest possible way**. One downside is longer build times
	- Deferred SSG: only difference from SSG is that developers can defer building certain pages until the first time a user requests it
	- static renders can be deployed to multiple [[Content Delivery Network (CDN)]]s to take advantage of edge-caching
	- individual HTML files must be generated for every possible URL. this can be challenging or infeasible
	- to combat long build times, Next.js provides Incremental Static Regeneration (ISR)
- Pre-rendering: running a client-side application at build time to capture its initial state as static HTML
- Server-side rendering (SSR): each web page is served to a site visitor at runtime, i.e. a portion of the build process happens on each page request. Visitors will always get the latest content from the server, but may have to wait a few seconds for it to display
	- avoids additional round-trips for data fetching and templating
- Hydration (or rehydration): client-side JS converts a static HTML web page (delivered via SSG or SSR) into a dynamic web page by attaching event handlers to the HTML elements
- Client-side rendering (CSR): rendering pages directly in the browser with JS
	- can be difficult to get and keep fast for mobile


Resources
- https://web.dev/rendering-on-the-web/
- https://www.gatsbyjs.com/docs/conceptual/rendering-options/
- https://www.joshwcomeau.com/react/the-perils-of-rehydration/

#web