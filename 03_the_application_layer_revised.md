# INTRO TO HTTP

## What to focus on
- Develop a clear understanding of the role of HTTP (it doesn't function in isolation)
- Break things down into individual components; break down concepts like HTTP and URLs into specific components & understand the purpose of each of those components


## The Application Layer
Protocols here structure messages, making sure they contain the appropriate data, and rely on protocols in the lower layers to get messages where they need to go.

Applications interact most with the protocols at this layer but can interact directly with the Transport Layer (e.g. by opening a TCP socket). Less common for apps to interact with layers below transport.


### Application Layer Protocols
Rules for how applications talk to each other at a syntactical level. Different apps have different requirements for how they communicate at a syntactical level.
For example, an email client and an email server need SMTP and POP or IMAP because they interact differently, than a web browser for a web server, which needs HTTP.


## HTTP and the Web
*Internet* a network of networks, the infrastructure that allows inter-network communication using both the physical network and lower layer protocols (i.e. Ethernet, IP, TCP/UDP)

The *World Wide Web* aka the web, is:
- An information system that we access using the internet, and that we navigate using URLs.
- Applications interacting with the web's resources primarily use HTTP 

Problem back in the 80s: 
Info stored on different computers is hard to locate &access. Although part of the same LAN, each computer required the user to log in directly and use a specific program/command.

The solution: 
Create a uniform system used by all hosts on the network.
- Structure information that can be rendered for viewing (HTML)
- Address resources so they can be easily located (URIs)
- Request a particular resource and (HTTP)
- Respond to a request for a specific resource (HTTP)

*Hypertext Markup Language* (HTML): structures resources
*Uniform Resource Identifier* (URI): a string of characters that identify particular resources.
> URI is part of a system that uniformly addresses resources on the web
URL is a way to find resources on the web
*Hypertext Transfer Protocol* (HTTP): rules that govern the way resources on the web are transferred between applications, i.e., requests and responses to requests


## BOOK: Intro to HTTP
### Background
#### Background
A browser is an interface, it's how we interact with the web.

HTTP is an application protocol that: 
- Sends a collection of files (CSS, HTML, Javascript, videos, images, etc) from a **server** to our browswer (the **client**)
- Serves as a link between applications and the transfer of hypertext documents (documents of text interconnected by hyperlinks).

*DNS* is a distributed database that keeps track of doman names and their corresponding IP addresses on the internet. The address is what's used to make a request to the server.

Web Browsers, an application (client), issue HTTP requests and process the HTTP response. Content being requested is located on a remote computer called a server. Servers are machines/devices capable of handling inbound requests, and their job is to issue a response back. Often, the response they send back contains relevant data specified in the request.

Resource, a generic term for things you interact w/ on the Internet via a URL; images, videos, web pages & other files. Resources aren't limited to files and web pages, they can also be in the form of software that lets you trade stock or play a video game.

A protocol is said to be **stateless** when it's designed in such a way that each request/response pair is completely independent of the previous one and those that come after.

**Key Takeaway**
Although an application may feel stateful, underneath the hood, the web is built on HTTP, a stateless protocol. Being stateless is what makes the web so:
+ resilient (flexible), 
+ distributed (shared, spread out, far reaching?), and 
- hard to control
- difficult to secure
- difficult to build on top of

#### What is a URL?
A URL (Uniform Resource Locator) is a subset of URI and, like an address, it's used to navigate the web to locate resources.

It's the most frequently used part of the general concept of a Uniform Resource Identifier or URI, which specifies how resources are located.

URL COMPONENTS
The URL, "http://www.example.com:88/home?item=book", can be broken into 5 parts:

1. **http**: The scheme. 
- It always comes before the `:` and `//` and tells the web client how to access the resource. Here, it tells the web client to use the Hypertext Transfer Protocol or HTTP to make a request. 
- Other popular URL schemes are ftp, mailto or git. 
- This part of the URL is sometimes referred to as the protocol, and there is a connection between the two in that the scheme can indicate which protocol (or system of rules) should be used to access the resource; in the context of of a URL however, the correct term for this component is the scheme.

2. **www.example.com**: The host. 
- It tells the client where the resource is hosted or located.

3. **88**: The port or port number. 
- It is only required if you want to use a port other than the default.
- ! This part of the URL is optional.

4. /home/: The path. 
- It shows what local resource is being requested. 
- ! This part of the URL is optional.

5. ?item=book: The query string, which is made up of query parameters. 
- It's used to send data to the server. 
- ! This part of the URL is also optional.

Sometimes, the path can point to a specific resource on the host.
- www.example.com/home/index.html points to an HTML file located on the example.com server.

Sometimes, we may want to include a port number which the host uses to listen to HTTP requests. 
- A URL in the form of: http://localhost:3000/profile is using the port number 3000 to listen to HTTP requests.
- Unless a different port number is specified, port 80 will be used by default in normal HTTP requests.

QUERY STRING/PARAMETERS
http://www.example.com?search=ruby&results=10

Query String Component - Description
* ?	- This is a reserved character that marks the start of the query string
* search=ruby	- This is a parameter name/value pair.
* &	- This is a reserved character, used when adding more parameters to the query string.
* results=10 - This is also a parameter name/value pair.
How the server uses these parameters is up to the server side application.

Because query strings are passed in through the URL, they are only used in HTTP GET requests.
Whenever you type in a URL into the address bar of your browser, you're issuing HTTP GET requests.

Query strings are great to pass in add'l info to the server, however, there are some limits to the use of query strings:
* Query strings have a max length. So, a lot of data can't be passed on with query strings.
* The name/value pairs used in query strings are visible in the URL. Passing sensitive info (e.g., username or password) to the server in this manner is not recommended.
* Space and special characters like `&` can't be used with query strings, they must be URL encoded.

URL ENCODING
- URLs were designed to accept only certain characters in the standard 128-character ASCII character set. 
- Reserved or unsafe ASCII characters which are not being used for their intended purpose and characters not in this set, have to be encoded. 
- URL encoding replaces these non-conforming characters with a `%` symbol followed by two hexadecimal digits that represent the ASCII code of the character.

Some popular encoded characters and example URLs:
Character	| ASCII code | URL
  Space	  |     20	   | http://www.thedesignshop.com/shops/tommy%20hilfiger.html
    !	    |     21   	 | http://www.thedesignshop.com/moredesigns%21.html
    +	    |     2B   	 | http://www.thedesignshop.com/shops/spencer%2B.html
    #	    |     23   	 | http://www.thedesignshop.com/%23somequotes%23.html

Characters must be encoded if:
1. They have no corresponding character within the standard ASCII character set.
2. The use of the character is unsafe because it may be misinterpreted, or even possibly modified by some systems. - e.g. `%` is unsafe because it can be used for encoding other characters. 
- Other unsafe characters include spaces, quotation marks, the `#` character, `<` and `>`, `{` and `}`, `[` and `]`, and `~`, among others.
3. The character is reserved for special use within the URL scheme, their presence in a URL serves a specific purpose. 
- Characters such as `/`, `?`, `:`, `@`, and `&` are all reserved and must be encoded. 
- e.g. `&` is reserved for use as a query string delimiter. 
- `:` is also reserved to delimit host/port components and user/password.

What characters can be used safely within a URL? 
- Only alphanumeric, special characters `$-_.+!'()"`, and reserved characters when used for their reserved purposes can be used unencoded within a URL. 
- If a character is not being used for its reserved purpose, it has to be encoded.

### HTTP
#### Making Requests
REQUEST METHODS
*HTTP Request Method*, the verb that tells the server what action to perform on a resource (GET, POST, etc,)
*Status*, the response status for each request.
- requests either time-out or get a response (even if the response is an error)

GET REQUESTS
- GET requests are used to retrieve a resource, and most links are GETs.
- The response from a GET request can be anything, but if it's HTML and that HTML references other resources, the browser will automatically request those referenced resources. A pure HTTP tool will not.

POST REQUESTS it's pros are a query strings cons
- POST requests are used to send or submit data to the server  
- HTTP body, how the data we're sending is being submitted to the server without going thru the URL. The body contains the data that is being transmitted in an HTTP message and is optional.

HTTP HEADERS
Allow the client and the server to send add'l info during the request/response HTTP cycle.
Headers are colon-separated name-value pairs that are sent in plain text

REQUEST HEADERS
Contain additional meta-information about the client and the resource being requested.

SUMMARY
The most important components to understand about an HTTP request are:
* HTTP method (req)
* path (req)
* headers (only the `Host` header req)
* message body (for POST requests)

#### Processing Responses
INTRODUCTION
*response*, raw data returned by the server

STATUS CODES
*status code*, a three-digit number the server sends back after receiving a request, signifying the status of the request.
Status Code	| Status Text	| Meaning
200	| OK | Request was handled successfully.
302	| Found | Requested resource has changed temporarily. Usually results in a redirect to another URL.
404	| Not Found	| Requested resource cannot be found.
500	| Internal Server Error	| Server has encountered a generic error.

302 Found
*redirect*, re-routing that occurs when a resource is moved. The request from the original URL is re-routed to a new URL.
When the browser sees a response status code of 302, it knows that the resource has been moved, and will automatically follow the new re-routed URL in the `Location` response header.

500 Internal Server Error
A server-side issue. The core problem can range from a mis-configured server setting to a misplaced comma in the application code.
Someone with access to the server will have to debug and fix the problem, which is why sometimes you see a vague error message asking you to contact your System Administrator.

RESPONSE HEADERS
Contain additional meta-information about the response data being returned.

SUMMARY
The most important parts of an HTTP response are:
* response line!?!?
* status code (req)
* (optional) headers
* (optional) message body, which contains the raw response data

#### Stateful Web Applications
A STATEFUL APP
When the server seems to remember your username for example and dynamically displays it on the page even after sending a new request (i.e. clicking different links on the same site). It's how items stay in your shopping cart as you keep adding items to it; t's how Gmail identifies you and displays your name and some customized greeting.
Some techniques being employed by web developers to simulate a stateful experience (mimic statefulness); sessions, cookies, and AJAX.

SESSIONS
When the server sends a unique token to the client called a *session identifier*. Whenever a client makes a request to that server, the client appends this token as part of the request, allowing the server to identify clients.

Faux statefulness has several consequences:
1. Every request must be inspected to see if it contains a `session id`. 
2. If the request does contain a `session id`, the server must check that the `session id` is still valid. The server needs to maintain some rules with regards to how to handle session expiration and also decide how to store its session data. 
3. The server needs to retrieve the session data based on the session id.
4. The server needs to recreate the application state (e.g., the HTML for a web request) from the session data and send it back to the client as the response.

COOKIES aka 'HTTP Cookies'
One common way to store session information. It's a piece of data, small files, containing the session information that's sent from the server and stored in the client, the browser, during a request/response cycle.

The actual session data is stored on the server. The client side cookie is compared with the server-side session data on each request to identify the current session.

The session id is stored on the client, and it is used as a "key" to the session data stored server side.
It is unique and expires in a relatively short time.
If you were to close your browser and shut down your computer, the cookie information would still persist.

We've seen that the session data is generated and stored on the server-side and the session id is sent to the client in the form of a cookie.

AJAX (Asynchronous JavaScript and XML)
Displays dynamic content in web applications. It allows browsers to issue requests and process responses *without a full page refresh*
Ihe main thing to remember is that AJAX requests are just like normal requests: 
+ they are sent to the server with all the normal components of an HTTP request, and 
+ the server handles them like any other request. 
The only difference is that instead of the browser refreshing and processing the response, the response is processed by a callback function, which is usually some client-side JavaScript code.

#### Security
SECURE HTTP (HTTPS)
Every request/response is encrypted before being transported on the network. This means if a malicious hacker sniffed out the HTTP traffic, the information would be encrypted and useless.
HTTPS sends messages through a cryptographic protocol called TLS for encryption. Earlier versions of HTTPS used SSL (Secure Sockets Layer) until TLS was developed. Cryptographic protocols use certificates to communicate with remote servers and exchange security keys before data encryption happens.

SAME-ORIGIN POLICY
An important concept that: 
+ permits unrestricted interaction between resources originating from the same origin, but 
- restricts certain interactions between resources originating from different origins.

*origin* is the combination of a url's scheme, hostname, and port
- `http://mysite.com/doc1` same origin as `http://mysite.com/doc2`
- `http://mysite.com/doc1` different origin to `https://mysite.com/doc2` (different scheme)
- `http://mysite.com/doc1` different origin to `http://mysite.com:4000/doc2` (different port)
- `http://mysite.com/doc1` different origin to `http://anothersite.com/doc2` (different host)

Exceptions include requests such as linking, redirects, or form submissions to different origins.
Also allowed is the embedding of resources from other origins, such as scripts, css stylesheets, images and other media, fonts, and iframes.

Cross-origin resource sharing (CORS), a mechanism that allows interactions that would normally be restricted cross-origin to take place. It works by adding new HTTP headers, which allow servers to serve resources cross-origin to certain specified origins.

**same-origin policy** is a cornerstone of web application security and an important guard against session hijacking attacks

The same-origin policy is an important concept that permits unrestricted interaction between resources originating from the same origin, but restricts certain interactions between resources originating from different origins.

SESSION HIJACKING
Threat: When an attacker gets a hold of the session id, both the attacker and the user now share the same session and both can access the web application. Here, the user won't even know an attacker is accessing his or her session without ever even knowing the username or password.

Countermeasures:
1. Resetting sessions, this is done with authentication systems. 
A successful login renders an old session id invalid and creates a new one. Here, on the next request, the victim will be required to authenticate. At this point, the altered session id will change, and the attacker will not be able to have access. Most websites implement this technique by making sure users authenticate when entering any potentially sensitive area, such as charging a credit card or deleting the account.

2. Setting an expiration time on sessions so that attackers don't have an infinite amount of time to pose as the real user.

3. Use HTTPS across the entire app to minimize the chance that an attacker can get to the session id.

CROSS-SITE SCRIPTING (XSS)
Background: This attack happens when users are allowed to input HTML or JavaScript that ends up being displayed by the site directly. Because the input box is just HTML <textarea>, users can input anything like raw HTML or Javascript to submit to the server. If server-side code doesn't sanitize the input, it'll be injected into the page content and *the browser will interpret the HTML and JavaScript and execute it.*

Threat: Attackers can craft malicious HTML and JavaScript that's destructive to both the server and future visitors of the page. For example, an attacker can use JS to grab the session id of every future visitor of this site and come back to assume their identity. 

**Note** the malicious code would bypass the same-origin policy because the code lives on the site.

Countermeasures:
1. Making sure to always sanitize user input. Eliminate problematic input, such as:  <script> tags, or using a safer input format over HTML and JavaScript, like Markdown.

2. Escape all user input data when displaying it. If HTML and JavaScript are needed input formats, then when you print it out, escape it so that the browser does not interpret it as code.
**Escaping**
To escape a character means to replace an HTML character with a combination of ASCII characters, called *HTML entities*, that tells the client to display that character as is and to not process it.


## Some Background and Diagrams
It's important to establish a mental model of "where" you are when analyzing a piece of code. The ability to zoom in to the details while also being able to recognize where you are in the larger picture is crucial to piecing together the jigsaw puzzle of web development.

The following will help you set up an initial mental model of how *server-side* development works

### Client-Server
HTTP, a stateless protocol for how clients communicate with servers.

The word "server" is severely overloaded, so it's important to keep in mind what exactly we're talking about at every turn. Each server components may be distributed across many physical machines and each of them could itself be comprised of multiple machines. There could also be many other intermediary machines, like load balancers, etc; large server infrastructures run into the hundreds or thousands of machines.


Zooming into the 'server' diagram. There are 3 primary server-side infrastructure pieces: a web server, an application server and a data store.

A *web server* is typically a server that responds to requests for static assets: files, images, css, javascript, etc. These requests can be handled by a simple web server because they don't require data processing.

An *application server*, is typically where application or business logic resides, and is where more complicated requests are handled. **This is where your server-side code lives when deployed.**

The application server will often consult a persistent *data store*, like a relational database, to retrieve or create data. Data stores can also be simple files, key/value stores, document stores and many other variations, as long as it can save data in some format for later retrieval and processing.

### HTTP over TCP/IP
Zooming into the http request / http response arrows.

           TCP/IP Connection
------ GET /index.html HTTP/1.1 ------>
<----- "<html><body>My Homepage</body></html>" ------

HTTP operates at the application layer and is concerned with structuring the messages that are exchanged between applications; it's actually TCP/IP that's ensuring the request/response cycle gets completed btwn the browser and the server.


## URLs
The distinction between URL and URI can be confusing. In fact, the terms are often used interchangeably.
A URL is a *subset* of URI that includes the network location of the resource. Technically, something like `https://launchschool.com/forum` could be referred to as both a URL and a URI. For ease of communication though it's probably best to just stick with URL, since this is a more specific description.

**For our purposes, you don't have to understand the exact differences between a URI and a URL; as far as we're concerned in HTTP, everything is a URL, but some sources may talk about URIs.**

### Schemes and Protocols
The convention is to refer to scheme names in lowercase, e.g. `http`, and protocol names in uppercase, e.g. `HTTP`
The scheme identifies which protocol should be used to access the resource.
Referring to a scheme as the protocol is technically incorrect.

### URLs and Filepaths
What Server-side and client-side frameworks have in common is that the way the path portion of the URL is used is determined by the application logic, and doesn't necessarily bear any relationship to an underlying file structure on the server.


## The Request/Response Cycle
**GET requests should only retrieve content from the server.** They can generally be thought of as "read only" operations, however, there are some subtle exceptions to this rule. For example, consider a webpage that tracks how many times it is viewed. GET is still appropriate since the main content of the page doesn't change.

**POST requests involve changing values that are stored on the server.** Most HTML forms that submit their values to the server will use POST. Search forms are a noticeable exception to this rule: they often use GET since they are not changing any data on the server, only viewing it.


## Summary
* *URL encoding* is a technique whereby *certain characters* in a URL are *replaced with an ASCII code*.

* URL encoding is used if a character has no corresponding character in the ASCII set, is unsafe because it is used for encoding other characters, or is reserved for special use within the url.

* A single HTTP message exchange consists of a *Request* and a *Response*. The exchange generally takes place between a *Client* and a *Server*. The client sends a Request to the server and the server sends back a Response.

* An *HTTP Request* consists of a *request line*, *headers*, and an optional *body*.
** *request line* is made up of the HTTP Method, path and HTTP version
** *headers* were optional but a/o version 1.1 the host header is required

* HTTP is *inherently insecure*. Security can be increased by using *HTTPS*, enforcing *Same-origin policy*, and using techniques to prevent *Session Hijacking* and *Cross-site Scripting*.

## Quiz
In what ways can we pass information to the application server via the URL?
Via the path and parameters