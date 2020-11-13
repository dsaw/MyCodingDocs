## [] Cross Origin Resource Sharing Notes!

* ### What is CORS?
	* **Cross Origin Resource Sharing** - HTTP mechanism using headers with which servers specify which origins can access the data in a browser. Most browsers restrict cross-origin requests - Same origin policy is followed where web app request resources from the the same origin the app was loaded from.
	Fetch & XMLHttpRequest follows CORS.
	* **Purpose** - To mitigate security risks like XSS attacks that can happen if a script on A.com fetches untrusted script from B.com.
	* **Basic overview** - browser sends a 'pre-flight' request to determine which methods and origins are allowed to send that cross origin request from the server. For simple GET/HEAD requests with specific set of allowed headers, a simple request is sent.

* ## Bypass CORS
	* Use JSONP (Json with Padding)
	* Use a proxy server
	* disable through extension during dev

	
	