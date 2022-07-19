- AJAX = asynchronous JavaScript and XML
- with AJAX, web applications can send and retrieve data from a server asynchronously without interfering with the display/behavior of the existing page
- [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest)) (XHR) JavaScript API
	- XHR can be used with protocols other than HTTP, and data can be in the form of XML, JSON, HTML, or plain text
	- The XHR spec is maintained as a [living standard](https://xhr.spec.whatwg.org/#:~:text=Abstract,a%20client%20and%20a%20server.)
- [`fetch()`](https://web.dev/introduction-to-fetch/) is a modern replacement for XHR.
	- [Living standard](https://fetch.spec.whatwg.org/)
	- The fetch API uses JavaScript [`Promises`](https://web.dev/promises/)
	- You can use `fetch` to send POST requests by setting the `method` and `body` parameters.
	- If you want to send credentials (e.g. cookies) with a `fetch` request, you can set:
```
  fetch(url, {
	  credentials: 'include'
  })
```
- Libraries for AJAX
	- jQuery
	- [Axios](https://axios-http.com/docs/intro)
		- promise-based HTTP client for node.js and the browser. Server-side, it uses the native node.js `http` module. In the browser, it uses XMLHTTPRequests
		- supports the `Promise` API
