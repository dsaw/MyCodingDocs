## [] Difference between localStorage, session storage & cookies.

* ### Local storage
	* Maintains a storage area for each origin that persists even when the browser is closed and reopened
	* No expiration date, but can be cleared through JS.
* ## Session storage
	* Maintains a storage area for each origin for the duration of the page session.
	* At most 5 MB, storage limit.
    * Neither local/session storage is sent to the server, while cookies are.

* ## Cookies
    * Used for personalization, tracking user behaviour & session management - a way for server to send state information to a user agent which can mantai/ modify it and send back.
    * Has a limit of 4KB.
    * has the form of string key-value pairs.
    * Server sends cookies in `Set-Cookie` header with parameters `Domain`, `Path` to define where the user agent can send back after storing them.
    * Server can specify the attribute `expires` for wishing the user agent to make the cookie persist for a long time. Note the user agent can delete the cookie if the user manually wishes to or quota of cookie is full.


# Security
    * Above methods are vulnerable to CSRF and XSS attacks. 