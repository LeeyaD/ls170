# URLs
### Be able to identify the components of a URL, including query strings
65. **What is a URL and what components does it have?**
A URL (Uniform Resource Locator) is a subset of URI and, like an address, it's used to navigate the web to locate resources.
Its components include: *port*, *path*, and *query string*.
- 1. http: The scheme. 
- -> Always comes before `:` and `//` and tells the web client how to access the resource. Here, it tells the web client to use the Hypertext Transfer Protocol or HTTP to make a request. 

- 2. *www.example.com*: The host or hostname.
- It tells the client where the resource is hosted or located.

- 3. 88: The port or port number. ()
- It is ONLY REQUIRED IF you want to use a port other than the default.

- 4. /home/: The path. (OPTIONAL)
- -> It shows what local resource is being requested by pointing to a specific resource on the host.

- 5. ?item=book: The query string, which is made up of query parameters. (OPTIONAL)
- -> It's used to send data to the server. 


70. **What is URI?**
The Uniform Resource Identifier (URI) is a a string of characters that identify particular resources within an information space.

66. **What is a Query string? What it is used for?**
An optional component in a URL, it's a string made up of one or more query parameters that gets passed in to GET requests only. The reserve char `?` marks the start of a query string and each parameter is a name/value pair separated by `=`. If there's more than one parameter, the reserved character `&` is used to separate them. 
Query strings are used to pass add'l info to the server, how the server uses the info is determined by the server side application.

**What are the limits of a Query strings?**
- 1. They have a max length, so a lot of data can't be passed on through them.
- 2. The name/value pairs used in query strings are visible in the URL. Passing sensitive info (e.g., username or password) to the server in this manner is not recommended.
- 3. Space and special characters like `&` can't be used with query strings, they must be URL encoded.

### Be able to construct a valid URL

### Have an understanding of what URL encoding is and when it might be used
67. **What URL encoding is and when is it used?**
A technique whereby *certain characters* in a URL are *replaced with an ASCII code*.
It's used if a character:
- has no corresponding character in the ASCII set, 
- is unsafe because it is used for encoding other characters, or 
- is reserved for special use within the url.

101. **What is the relationship between a scheme and a protocol in the context of a URL?**
The scheme identifies which protocol (or system of rules) should be used to access the resource.
For example, in http://www.viki.com, the scheme (http) tells my web browser to use the Hypertext Transfer Protocol (HTTP) to make a request. 

# HTTP AND THE REQUEST/RESPONSE CYCLE
* Give an overview of the Application layer
Application: end-to-end communication between applications

64. **What is HTML?**
Standing for Hypertext Markup Language, it's a uniform system used by all of the hosts on the network, to structure information that could be rendered for viewing

72. **What is HTTP? and what is its role?**
Hypertext Transfer Protocol is a set of rules that control the way resources on the web are transferred between applications (i.e. requests and responses to requests).


### Be able to explain what HTTP requests and responses are, and identify the components of each
75. **What are HTTP requests? What are its components?**
An HTTP request is request by the client
It consists of:
- request line is made up of the HTTP Method, path and HTTP version
- headers, were optional but a/o version 1.1 the host header is required, and
- an optional *body*.

**What is an HTTP Method?**
A value that identifies the kind of HTTP request.

75. **What are HTTP responses? What are its components?**
An HTTP response is what the server returns to the client in response to an HTTP request. 
It consists of: 
- a status line, 
- optional *headers*, that contain meta-data in the form of key:value pairs that provide add'l info about the response and
- an optional *body*.

87. **What is the HTTP response body and what do we use it for?**
It's optional and if used, it'd contain the raw response data being requested.

87. **What is the HTTP headers and what are they used for?**
Headers contain meta-data in the form of colon-separated name-value pairs sent as plain text in a request or response. They allow the client to send add'l info regarding their request and the server to send add'l info regarding its response.


### Be able to explain what status codes are, and provide examples of different status code types
**What is a status code? What is the purpose of status codes?** 
It's a three-digit number the server sends back after receiving a request, it signifies the status of the request.

**What are some of the status codes types?**
200 is `ok` and means the request was successfully handled.
Codes in the 300s means the resource was `found` but that you were redirected to another URL because it's address was changed
Codes in the 400s mean `not found` and that the resource being requested couldn't be found.
Codes in the 500s mean `internal server error` and that a server-side error occurred
302	| Found | Requested resource has changed temporarily. Usually results in a redirect to another URL.
404	| Not Found	| Requested resource cannot be found.
500	| Internal Server Error	| Server has encountered a generic error.


### Understand what is meant by 'state' in the context of the web, and be able to explain some techniques that are used to simulate state
77. **What is a state in the context of the 'web'?**
When the server seems to remember you and what you've done with the web page you're on reflecting it. 
For example, when you add items to your shopping card on Amazon even after you click on different links (i.e. send new requests) to look at different items on Amazon. Or logging into your bank account and seeing a greeting, with your name, being displayed as you conduct your financial business (i.e. send new requests).

78. **What is statelessness?**
See answer below.

82. **HTTP is a 'stateless' protocol, what does that mean exactly?** 
This means that each Request/ Response cycle is independent of Request and Responses that came before or those that come after.
- HTTP cannot persist information in either a request or a response.
- Each request/response cycle is independent of the previous and next cycles.
- Each request should contain all the information necessary for the request to be fulfilled.

80. **How can we mimic a stateful application?**
Through techniques which use *session IDs*, *cookies*, and *AJAX*.
- By using sessions. == session IDs
When the server sends a unique token, that expires in a relatively short time, to the client called a *session identifier*. Whenever a client makes a request to that server, the client appends this token as part of the request, allowing the server to identify clients.

Faux statefulness has several consequences:
1. Every request must be inspected to see if it contains a `session id`. 
2. If the request does contain a `session id`, the server must check that the `session id` is still valid. The server needs to maintain some rules with regards to how to handle session expiration and also decide how to store its session data. 
3. The server needs to retrieve the session data based on the session id.
4. The server needs to recreate the application state (e.g., the HTML for a web request) from the session data and send it back to the client as the response.

- By using cookies. == cookies
It's a piece of data containing the session ID that's sent from the server and stored in the client, the browser, during a request/response cycle.

Actual session data is stored on the server. The client side cookie is compared with the server-side session data on each request to identify the current session.

The session data is generated and stored on the server-side and the session id is sent to the client in the form of a cookie.

- By sending data as parameters through the URL. = AJAX???
It allows browsers to issue requests and process responses *without a full page refresh*


### Explain the difference between GET and POST, and know when to choose each
A GET is used to retrieve information, while a POST request is for sending information to a server.
- For example, GET is used to load a web page for viewing. POST is used for logging in.

**What are the benefits of using a POST request over a Query String?**
- 1. They don't have a max length, so a lot of data can be passed on through them.
- 2. The information they're passing isn't visible in the URL, so passing sensitive info is possible.
- 3. URL encoded isn't needed since there are no unsafe or reserve characters.

90. **Which HTTP method would you use to send sensitive information to a server? Why?**
POST because the information being passed isn't visible in the URL.

**Compare HTTP and HTTPS.**
Every request/response is encrypted through the Transport Layer Security protocol before being transported on the network.


# SECURITY
### Have an understanding of various security risks that can affect HTTP, and be able to outline measures that can be used to mitigate against these risks
HTTP is inherently insecure. Security can be increased by using HTTPS, enforcing Same-origin policy, and using techniques to prevent Session Hijacking and Cross-site Scripting.

98. **Describe some of the security threats and what can be done to minimize them?**
1. Session Hijacking
Threat: If an attacker gets a hold of the session id, they can access the same session as the user without ever knowing the username or password. Both can access the web application and the user won't even know an attacker is accessing their session.

Countermeasures:
- 1. Resetting sessions, this is done with authentication systems. 
A successful login renders an old session id invalid and creates a new one. Here, on the next request, the victim will be required to authenticate. At this point, the altered session id will change, and the attacker will not be able to have access. Most websites implement this technique by making sure users authenticate when entering any potentially sensitive area, such as charging a credit card or deleting the account.

- 2. Setting an expiration time on sessions so that attackers don't have an infinite amount of time to pose as the real user.

- 3. Use HTTPS across the entire app to minimize the chance that an attacker can get to the session id.

2. Cross-site Scripting
Threat: Attackers can create malicious HTML and JavaScript when allowed to input HTML or JavaScript that ends up being displayed by the site directly because the input box is just HTML <textarea>. If server-side code doesn't clean the input, it'll be injected into the page content and the browser will interpret the HTML and JavaScript and execute it. This is harmful to both the server and future visitors of the page. 
For example, an attacker can use JS to grab the session id of every future visitor of this site and come back to assume their identity. 
**Note** the malicious code would bypass the same-origin policy because the code lives on the site.

Countermeasures:
1. Making sure to always clean user input. Eliminate problematic input, such as:  <script> tags, or use a safer input format over HTML and JavaScript, like Markdown.

2. Escape all user input data when displaying it. If HTML and JavaScript are needed input formats, then when you print it out, escape it so that the browser does not interpret it as code.
**Escaping**
To escape a character means to replace an HTML character with a combination of ASCII characters, called *HTML entities*, that tells the client to display that character as is and to not process it.


99. **What is HTTPS? How it is used to mitigate certain security threats?**  
A secure HTTP protocol that encrypts every request/response before they're transported on the network by sending messages through a cryptographic protocol called TLS for encryption. This means if a malicious hacker packet sniffed the HTTP traffic, the information would be encrypted and useless.

? Protocols like TLS use certificates to communicate with remote servers and exchange security keys before data encryption happens.

99. **What is the Same Origin Policy? How it is used to mitigate certain security threats?**  
The same-origin policy is an important concept that permits unrestricted interaction between resources originating from the same origin, but restricts certain interactions between resources originating from different origins.

An *origin* is the combination of a url's scheme, hostname, and port.

- `http://mysite.com/doc1` same origin as `http://mysite.com/doc2`
- `http://mysite.com/doc1` different origin to `https://mysite.com/doc2` (different scheme)
- `http://mysite.com/doc1` different origin to `http://mysite.com:4000/doc2` (different port)
- `http://mysite.com/doc1` different origin to `http://anothersite.com/doc2` (different host)

Exceptions include requests such as linking, redirects, or form submissions to different origins.
Also allowed is the embedding of resources from other origins, such as scripts, css stylesheets, images and other media, fonts, and iframes.

Cross-origin resource sharing (CORS), a mechanism that allows interactions that would normally be restricted cross-origin to take place. It works by adding new HTTP headers, which allow servers to serve resources cross-origin to certain specified origins.

**same-origin policy** is a cornerstone of web application security and an important guard against session hijacking attacks


### Be aware of the different services that TLS can provide, and have a broad understanding of each of those services
**What are the services TLS provides?**
There are three important security services that are provided by TLS: 
- 1. Encryption, a process of encoding a message so that it can only be read by those with an authorized means of decoding the message
- 2. Authentication, a process to verify the identity of a particular party in the message exchange and
- 3. Integrity, a process to detect whether a message has been interfered with or faked

**Explain Encryption**
A process of encoding a message so that it can only be read by those with an authorized means of decoding the message

**Explain Authentication**
A process to verify the identity of a particular party in the message exchange
TLS Authentication uses digital certificates as a means of identification.
TLS Authentication relies on a 'chain of trust'.

**Explain Integrity**
A process to detect whether a message has been interfered with or faked

**What is TLS Handshake?**
The process by which TLS sets up the initial secure (encrypted) connection.

It encrypts each HTTP request/response in a such a way that they can only be decrypted by the intended recipient. 
TLS uses a combination of symmetric and asymmetric cryptography, though most message exchange is done via symmetric key encryption, the initial symmetric key exchange is done using asymmetric key encryption.

TLS assumes TCP is being used at the Transport layer, and the TLS Handshake **takes place after the TCP Handshake**. A step-by-step description of the TLS Handshake process might look something like this:

1. The TLS Handshake begins with a `ClientHello` message sent immediately after the TCP `ACK`. Among other things, this message contains the maximum version of the TLS protocol that the client can support, and a list of Cipher Suites that the client is able to use (we'll discuss Cipher Suites a little later on).

2. Upon receipt of the `ClientHello` message, the server responds with a message of its own. This message includes a `ServerHello`, which sets the protocol version and Cipher Suite, as well as other related information. As part of this message the server also sends its certificate (which contains its public key), and a `ServerHelloDone` marker which indicates to the client that it has finished with this step of the handshake.

3. Once the client has received the `ServerHelloDone` marker, it will initiate the key exchange process. It's this key exchange process that enables both the client and server to securely obtain a copy of the symmetric encryption key that'll be used for most of the secure message transfer between the two. The exact process for generating the symmetric keys will vary depending on which key exchange algorithm was selected as part of the Cipher Suite.

4. After the key exchange, the client and server can now begin secure communication using the symmetric key.


The TLS Handshake is a fairly complicated process and the exact process will vary according to which version of TLS is used. The key points to remember about the TLS Handshake process is that it's used to:

- Agree which version of TLS to be used in establishing a secure connection.
- Agree on the various algorithms that will be included in the cipher suite.
- Enable the exchange of symmetric keys that will be used for message encryption.

Because of it's complexity it does impact performance. The TLS handshake can add up to two round-trip of latency (depending on the TLS version) to the establishment of a connection between client and server prior to the point where any application data can be sent. This is on top of the initial round trip resulting from the TCP Handshake.

**Note:** there is a protocol called Datagram Transport Layer Security (DTLS), which is based on TLS. This protocol is specifically for use with network connections which use UDP rather than TCP at the Transport layer.

**What is symmetric key encryption? What is it used for?**
Used to exchange messages securely, symmetric key encryption is a shared key system meaning both sender and receiver share a common encryption key. This same key is used by both sender and receiver to encrypt and decrypt messages, respectively.

This system relies on the sender and receiver both having access to the key and no one else being able to access it. 

ISSUE: How do sender and receiver exchange encryption keys in the first place? In person, and so over the internet is not an option because if the key is sent in a readable format to the other party in our message exchange, but was intercepted by a third-party, it could then be used to decrypt any subsequent messages between the sender and receiver.

SOLUTION: A mechanism whereby we can encrypt the encryption key itself, so that even if it is intercepted it can't be used.

**What is asymmetric key encryption? What is it used for?**
Asymmetric key encryption, aka 'public key encryption', uses a pair of keys: a public key, and a private key.
 
In this asymmetric system, the keys in the pair are non-identical: 
- the public key is used to encrypt and 
- the private key to decrypt.

* Messages encrypted with the public key can only be decrypted with the private key. The public key is made openly available but the private key is kept in the sole possession of the message receiver.

Alice wants to receive encrypted messages. She generates a public key and a private key. She makes the public key available but keeps the private key to herself. Bob uses Alice's public key to encrypt a message and send it to Alice. Alice decrypts Bob's message using her private key.

* This encryption is primarily intended to work in one direction. Bob can send Alice messages encrypted with the public key which she can then decrypt with the private one.

**Describe the pros and cons of TLS Handshake**
+ It's the `secure` in HTTPS 
- its complexity has an impact on performance. It can add up to two round-trip of latency (depending on the TLS version) when establishing a connection between client and server prior to any application data being sent. This is in addition to the initial round trip of latency from the TCP Handshake.

**Why do we need digital TLS/SSL certificates?** 
TLS Authentication uses digital certificates as a means of identification.

**What is it CA hierarchy and what is its role in providing secure message transfer?**
CAs digitally sign the certificates they issue, generating a signature using their own private key.
Before issuing a certificate, CAs verify that whoever is requesting the certificate is who they claim to be.

There are many CAs, most of them are Intermediate CAs, with a small, trusted group of Root CAs.
Certificates are generally signed by one CA. An Intermediate CA will sign an end-user's certificate, and a Root CA will sign the Intermediate CA's certificate. This creates the 'chain' in the chain of trust.

**What is Cipher Suites and what do we need it for?**
A set of cryptographic algorithms, ciphers, that perform encryption, decryption, and other related tasks.
These various ciphers are used by TLS to establish and maintain a secure connection, i.e. perform the key exchange process, carrying out authentication, symmetric key encryption, and check message integrity.

**How does TLS add a security layer to HTTP?**
It encrypts every HTTP request/response before they're transported on the network.

----------------------------------------------------------------------------------------------------

# MISC
3. **Is the Internet the same thing as a network?**
4. **What is WEB (world wide web)**
An information system of resources that sits on the internet and can be navigated via URLs.

5. **What is the difference between network, Internet, and WEB?**
**Give examples of some protocols that would be used when a user interacts with a banking website. What would be the role of those protocols?** 

**In the context of network protocols, what is *encapsulation*?** - ADDED
It's when data from one one layer is being hid in the PDU, specifically the data payload, of the layer below it. 

**Why is data encapsulation important?** - ADDED
It provides a level of abstraction, creating separation between protocols operating at different network layers. It allows protocols to work together without being concerned about each others' implementation. They just needs to encapsulate data from the layer above and provide the result of the encapsulation to the layer below.

**What are well-known models that demonstrate network communication as a layered system? and what are their layers?** - ADDED
The OSI and TCP/IP models breakdown network communication into layers where protocols are grouped by what they address. The OSI model groups protocols by the function they provide and has 7 layers. From bottom to top; physical > data link > network > transport > session > presentation > application. 

Meanwhile the TCP/IP (IP Suite) model groups protocols by their scope of communication and has 4 layers. From bottom to top; link > internet > transport > application.

**What is the purpose of having models like OSI and TCP/IP?** - ADDED
They break down the different parts of network communication into modules and structuring them in a layered system, which helps us better understand the protocols in each layer and get a clearer idea of how they work and how they're implemented. These models also give us a clear overview of how the internet works as a whole.

**What is a PDU? and what are its parts?** - ADDED
It's a block of code being transmitted over a network. It consists of: a header (and sometimes a trailer/footer), which contains protocol-specific metadata about the PDU and a data payload contains encapsulated data we want to transport.

A PDU has different names depending on the specific protocol being used at a particular layer; an Ethernet PDU is called a *frame*, an IP PDU is called a *packet* and a TCP or UDP PDU is, respectively, called a *segment* or *datagram*.

**Why are PDUs important?** - ADDED
They're how data encapsulation is implemented. The entire PDU from a protocol at one layer is set as the data payload for a protocol one layer below. 

**What is the relationship between PDU and Data Payload?** - ADDED
One gets encapsulated into the other, the entire PDU of a protocol at one layer is encapsulated into the data payload of the protocol one layer below.

**What is subnetting?** - ADDED
When networks are logically split into sub-networks with each subnetwork defined by a range of IP addresses available to it. Subnetting is a byproduct of the hierarchical structure of IP Addresses.

**Why do we need both MAC addresses and IP addresses?**
Because each of these types of addresses serve different purposes. Inter-network communication requires data to traverse multiple cables/wires or hops across multiple routers. IP addresses are needed because they're responsible for end-to-end communication, they identify the fact that data needs to go from my computer in Brooklyn to a server in California (i.e. devices on different networks). MAC addresses are needed because they're responsible for 
physical point-to-point communication between devices within the same network, they identify where the data currently is and which router it should be sent to next. It's at each router that the data is processed and given new source & destination MAC addresses, which thanks to IP addressing, help the data hop across multiple routers in the direction of and ultimately to its final end destination. 

* Give an overview of the Transport layer
Transport: end-to-end communication between networked applications; 2 important things it does is 
1. Establishing a connection between networked applications
2. Breaking down data from the application layer into segments/datagrams
2. Breaking down data from the application layer into segments/datagrams
Replying on network ports to put the segment/datagram pieces together and directs

* What are multiplexing and demultiplexing?
Multiplexing and demultiplexing provide the ability to transmit *multiple signals over a single channel* thru the use of *network ports*. Multiplexing is the breaking down and demultiplexing is the putting back to gether of these transmitted signals.

**What is pipelining protocols? What are the benefits of it?**

**What is a checksum and what is it used for? How is it used?**
It's an error checking value created by an algorithm. The destination device creates a value using the same algorithm and if it doesn't match, it drops the data.

51. **What does it mean that the protocol is connection-oriented?**

118. **What is server-side infrastructure? What are its basic components?**
There are 3 primary server-side infrastructure pieces: a web server, an application server and a data store.

A *web server* is typically a server that responds to requests for static assets: files, images, css, javascript, etc. These requests can be handled by a simple web server because they don't require data processing.

An *application server*, is typically where application or business logic resides, and is where more complicated requests are handled. **This is where your server-side code lives when deployed.**

The application server will often consult a persistent *data store*, like a relational database, to retrieve or create data. Data stores can also be simple files, key/value stores, document stores and many other variations, as long as it can save data in some format for later retrieval and processing.