- The `Link` component enables *client-side navigation* between pages. This means the page transition happens using [[JavaScript]], which is faster than the default browser navigation.
- Pre-rendering: Next.js pre-renders every page by default (generates the HTML ahead of time). Two forms of pre-rendering:
	1. Static Generation: generates HTML at build time
	2. Server-side Rendering: generates HTML on each request
	- *Note*: in development mode, pages are pre-rendered on every request
	- it's recommended to use static generation whenever possible (page can be built once and served by [[Content Delivery Network (CDN)]])
- Server-side Rendering
	- `getServerSideProps` called at request time
- Client-side rendering
	- useful when you don't require SEO, you don't need to pre-render, or data changes frequently. E.g. a private user dashboard
	- data is fetched at runtime
	- note: data is not cached
	- [SWR](https://swr.vercel.app/) (derived from `stale-while-revalidate`) is a React hook library for fetching data on the client side. It handles caching, revalidation, focus tracking, refetching on intervals, etc.

#web