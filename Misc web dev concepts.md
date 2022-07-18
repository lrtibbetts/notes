##### Static vs dynamic sites
- A static website is made up of a fixed number of pre-built files stored on a web server. When a user requests a page via a URL, the server returns the HTML specified by the URL and any accompanying CSS and/or JS files
- Dynamic websites don't store each page as its own HTML file. The web server builds pages on-the-fly. When the user requests a page, the server pulls information from one or more databases and constructs an HTML file


##### Server-side vs client-side rendering
- Server-side rendering (SSR) means the server generates a complete HTML page in response to a URL request
- Client-side rendering means the browser will compile and run JavaScript code to generate the HTML content


##### Template engines
- Enable you to use static template files in your application.
- At runtime, the engine replaces variables in a template file with actual values and transforms the template into an HTML file to be sent to a client.


##### AJAX and XHR
- AJAX = asynchronous JavaScript and XML
- with AJAX, web applications can send and retrieve data from a server asynchronously without interfering with the display/behavior of the existing page
- The [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest)) (XHR) JavaScript API is used to execute AJAX on webpages
	- XHR can be used with protocols other than HTTP, and data can be in the form of XML, JSON, HTML, or plain text
	- The XHR spec is maintained as a living standard


##### Single-page application (SPA)
- A web app implementation that loads only a single web document
- The current web page is rewritten with new data from the server, instead of the default method of a web browser loading entire new pages.