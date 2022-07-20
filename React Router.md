[[React]] Router
https://reactrouter.com/docs/en/v6/getting-started/concepts

3 main jobs:
- subscribing to and manipulating the history stack
- matching the URL to your routes
- rendering a nested UI from the route matches

Terminology
- URL: url in the address bar
- Location: object based on the built-in browser API `window.location`. represents "where the user is at". basically an object representation of the URL
- Location state: a value that persists with a location that *isn't* located in the url. stored invisibly in the browser's memory
- History Stack: built up as a user navigates
- Client Side Routing: HTML doc can link to other docs and the browser handles the history stack itself. CSR means developers can manipulate the history stack without making a document request to the server
- History: object that lets React Router subscribe to changes in the URL as well as manipulate the history stack programmatically
- Router: stateful, top-level component that makes all the other components work
- Route Config: tree of route objects
- Route: object typically with a shape of `{ path, element }` or `<Route path element>`
- Match: object that holds information when a route matches the URL
- Outlet: component that renders the next match in a set of matches

#web