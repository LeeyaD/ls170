# THE INTERNET
### Have a broad understanding of what the internet is and how it works
1. What is a network?** - ADDED
Two or more connected devices that can share data.

2. What is a local area network (LAN)?** - ADDED
A group of devices connected to each other via a switch or hub and located in one physical location.

3. What is a hub and what is it used for?** - ADDED
A network device that facilitates communication *within* a network. When it receives communication from one host, it duplicates it and sends it to all other connected hosts. Hosts that aren't the intended receiver simply ignore the data.

4. What is a switch and what is it used for?** - ADDED
A network device that facilitates communication *within* a network. When it receives communication from one host, it only sends it to the appropriate receiving host.

5. What is a router and what is it used for?** - ADDED
A network device that facilitates communication *between* networks.

6. What is a protocol?** - ADDED
A systems of rules.

7. What are network protocols?** - ADDED
Systems of rules that control the transmission of data over a network.

8. What makes up a network's infrastructure? (high-level picture)** - ADDED
Tangible pieces that facilitate network communication; i.e., network devices, routers, switches, cables, wires and even radio waves.

9. Why are there different types of protocols?** - ADDED
Because there are different types of protocols that deal with different areas of network communication (e.g., HTTP for structuring messages and TCP for transferring messages btwn. apps) and others that deal with the same areas of network communication but in a different way (e.g., TCP and UDP both transfer messages btwn. apps but they do it in different ways).

10. What is the internet?** - ADDED
A network of networks. It's made up of a *physical network* (networked devies, routers, switches, cables, etc.) and lower-level *protocols* that support it. It's the interaction of those protocols (Ethernet, IP, and TCP/UDP) via the physical network that facilitates communication between networked applications.

119. **What is a server? What is its role?** 
A host that can respond to a request for resources, it's role is to also provide the requested resource.


### Understand the characteristics of the physical network, such as latency and bandwidth
11. What are the characteristics/limitations of the physical network?** - ADDED
Latency and bandwidth. 

12. What is *latency*?** - ADDED
A measure of delay, it's the time it takes for data to travel from one point in a network to another. There are 4 types of delays that contirbute to the overall latency of a network: 
1. Propagation delay: which is what we think of when imagine latency, it's the time it takes for data to go from one point to another.
2. Transmission delay: the time it takes to push data onto a link (i.e. a wire or cable). The **Interframe Gap (IFG)**, specified by the Ethernet protocol  contributes to this delay, it's the brief pause between the transmission of each *frame* that allows the receiver to prepare to receive the next frame.
3. Processing delay: the time it takes data to be processed at every link since data doesn't directly cross from one cable to another.
4. Queuing delay: the time it takes data to queue/buffer, which occurs when there's more data being transmitted than a network device can processed at one time.

13. What are network 'Hops'?** - ADDED
When data is transmitted across multiple routers to get to the target host. Each 'hop' is data being transmitted from one link (i.e., one cable or wire) to another.

14. What is the relationship between network 'Hops' and latency?** - ADDED
Each 'hop' can increase latency due to *processing* and *transmission* delays, which is the time it takes data to be processed at and pushed onto a link (i.e. network wire/cable), repsectively.

15. What is *bandwidth*?** - ADDED
A measure of capacity, it's the amount of data that can be sent over a network connection in a set period of time (usually a second).

How can we as developers deals with the limitations of physical network?**
By being mindful of how we build our programs and what protocols we choose to implement in them. Understanding the trade-offs that come with each chosen protocol.


### Have a basic understanding of how lower level protocols operate
16. Explain how lower-level protocols work in general.
Lower-level protocols like Ethernet and Internet facilitate inter-network communication between devices on different networks thru their ability to encapsulate data from the protol layer above them and to route that data appropriately thru their different address schemes (MAC and IP addressing).

17. Give an overview of the physical layer - ADDED
The physical layer is where electrical signals, light signals, and radio waves, which carry network communications, are being transmitted across wires, cables, and wifi.

18. Give an overview of the Data Link/Link layer - ADDED
It's the interface between the physical network and the more logical layers above.

19. What is the Ethernet Protocol? - ADDED
A system of rules that controls physical point-to-point communication between devices within a network via *MAC addressing* and *frames*.

20. What are the Ethernet protocol's primary functions? - ADDED
  1. Using *MAC addressing* to identifying devices connected to a local network.
  2. Using *frames* (i.e., the Ethernet PDU) to move encapsulated data from the Internet/Network layer over the physical network btwn. the devices that make it up (i.e., hosts, switches, routers). 

21. What is a MAC address and what is its role in network communication?** - ADDED
It's a unique sequence of six 2-digit hexadecimal numbers that is (usually) permanently associated with a particular device and, therefore, sometimes referred to as a physical address. Re: network communication, MAC addresses are used to identify devices on a local network, facilitating physical point-to-point communication.

22. Why are MAC addresses unscalable?** - ADDED
Because there's no logical hierarchy, the entire address is one sequence of values that can't be broken down into sub-divisions. 

23. What is included in an Ethernet frame? - ADDED
Two important parts of an Ethernet frame are:
  1. A header containing, among other fields, the source and destination MAC Addresses. These addresses, respectively, represent the device that created the frame and the device the data is intended for. 
  2. A data payload containing the data for the entire PDU of the layer above, at this layer that data is an IP packet (an Internet Protocol Data Unit).

24. Give an overview of the the Network/Internet layer - ADDED
This layer makes inter-network communication between DEVICES possible NOT specific applications running on those devices.

25. What is the Internet Protocol?** - ADDED
A system of rules that controls end-to-end communication between DEVICES from different networks NOT specific applications running on those devices. It accomplishes this with 2 primary functions:
1. Using *packets* to encapsulate and move data from the transport layer (a TCP segment or UDP datagram) between devices on different networks.
2. Using *IP addressing* to logically route packets to a device on another network.
Note: There are two versions of IP currently in use: IPv4 and IPv6.


26. What's included in an IP packet?
A header and a data payload. 
The header contains information about the packet including the source and destination IP Addresses. 
The data payload contains encapsulated data from the Transport layer above; either a TCP segment or UDP datagram

27. What is a packet in computer networking?
A packet is found at the Internet or Network layer and is the Internet Protocol's Data Unit.


### Know what an IP address is and what a port number is
28. What is an IP address?
Identifiers for devices and servers (end-to-end), they're of a particular length of bits divided into sections that get converted from binary to decimal.
These addresses get assigned to devices when they join a network and fall within a range of addresses available to the LAN that the device is connected to.

IPv6 has more bits in its addresses and when compared to IPv4, has a different structure for the header. There's also no error checking, IPv6 leaves that to the Link Layer Checksum.

29. What are (network) ports?
A port is an identifier for a specific process or application running on a host.
Ports are used in the process of multiplexing and demultiplexing.
Source and destination port numbers are listed in Transport layer PDUs.

30. How do port numbers and IP addresses work together?
Together they enable end-to-end communication btwn specific applications on different machines.
The IP addresses in an IP packet header direct data from one host to another while the port numbers within the segment or datagram header is used to direct that data to specific processes on a host. 

31. What is a network socket?
- At a conceptual level it means the combination of IP address and port number that provides a communication end-point.
- At an implementation level it can refer to a socket object used to create connections between applications.

**How do sockets on the implementation level relate to the idea of protocols being connectionless or connection-oriented?**

33. How do transport layer protocols enable communication between processes?
Via sockets, a combination of a client's IP address and process port number.

### Have an understanding of how DNS works
39. **What is DNS and how does it work?**
Domain Name System, is a distributed database of domain names mapped to IP addressed. When it receives a DNS request, it looks up the IP address by the domain name given and returns it to the client's web browser so the HTTP request can be routed appropriately. 

### Understand the client-server model of web interactions, and the role of HTTP as a protocol within that model
The client-server model is two devices transmitting data over the network, each device having a certain role.
- The client is usually a web-browser responsible for issuing HTTP requests and processing responses in a way that is readable to humans (e.g. rendering the HTML of a web page).
- The server is a remote computer that can handle inbound requests. Its job is to issue an HTTP response, which ideally contains the resource requested by the client. If not, then a status code that explains what happened.
- NOTE: Here, the server refers to all the server-side infrastructure that processes the requests and provides the responses. E.g. web server > application server > data store

The role of HTTP as a protocol within this model is 


# TCP & UDP
* What is network reliability?
* The underlying network is *inherently unreliable*. If we want reliable data transport we need to implement a system of rules to enable it.

* What are the fundamental elements of reliable protocol?
In-order delivery; Message acknowledgement & retransmission; De-duplication, and Error Detection

* What does it mean that network reliability is engineered?
Network realiability is implemented by developers via the protocols chosen when applications are built. Even within protocols like UDP for example, developers can choose to use it as a base upon which to build certain realiabile features as they see fit like de-duplication but not in-order delivery or vice versa.

### Have a clear understanding of the TCP and UDP protocols, their similarities and differences
48. **Is TCP connectionless? Why?**
No, it's a *connection-oriented* protocol because in order to begin sending data it has to establish a connection using the *Three-way handshake*.

* What are the common benefits of both TCP and UDP?
- Both provide multiplexing and demultiplexing
- Both provide error detection

* What are the benefits & trade-offs of TCP?
- TCP establishes a connection using the *Three-way-handshake* before sending data
- TCP provides multiplexing and demultiplexing
- TCP provides reliability through:
  1. message *acknowledgement* and *retransmission* 
  2. *in-order delivery*
  3. de-duplication
  4. error detection
- TCP provides *Flow Control* and *Congestion Avoidance*

### Have a broad understanding of the three-way handshake and its purpose
* What is a three-way handshake? What is it used for?
To establish a TCP connection between two different applications.

* What are the advantages and disadvantages of the Three-way handshake?
+ It establishes a connection before any data is transmitted, increasing the realiabilty of our data transmissions.
- Establishing a connection before any data is transmitted increases the latency of our data transmisssions

### Have a broad understanding of flow control and congestion avoidance
* What is network congestion?
When there's more data being transmitted across the internet than the physical network can handle. Excess data that can't be handled get but in a buffer or queue and if the buffer overflows that data is dropped. 

* What is Congestion Avoidance?
Congestion avoidance is a process by which TCP uses data loss (based on the volume of retransmissions required) as a feedback mechanism to determine how congested the network is, and adjusts the amount of data being sent accordingly.

* What is Flow Control? How does it work and why do we need it?
Flow Control is a mechanism to prevent the sender overwhelming the receiver with more data than it can process. Each participant in a connection lets the other participant know how much data it is willing to accept using the WINDOW field in the TCP header.

- The main *downsides of TCP* are:
  1.  the *latency overhead of establishing a connection* and 
  2.  the potential *Head-of-line blocking* as a result of in-order delivery.

* What are the benefits & trade-offs of UDP?
- UDP is *connectionless*, so it doesn't need to establish a connection before it starts sending data
- UDP provides multiplexing and demultiplexing
- UDP provides error detection
- - UDP does provide error detection via a checksum, though this is optional if using IPv4.
- Although it is unreliable, the *advantage of UDP* is *speed* and *flexibility*.
- UDP isn't realiable as it does not provide:
  1. UDP doesn't provide message acknowledgement and retransmission
  2. UDP doesn't provide in-order delivery
  3. UDP doesn't provide de-duplication
- UDP doesn't provide *Flow Control* and *Congestion Avoidance*

55. **How does TCP facilitate efficient data transfer?**



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

### Be able to describe the HTTP request/response cycle
76. **Describe the HTTP request/response cycle.**
1. I enter a URL like http://www.viki.com into the address bar of my web browser, Chrome.
1. The browser, Chrome, creates an HTTP request, which is "packaged up" meaning the HTTP request is encapsulated into the data payload of the protocol in the transport layer below it, and so on to the next layer.
2. If Chrome or my Macbook already have a record of the IP address for the domain name, viki.com, in their DNS cache, it will use this cached address. If the IP address isn't cached, a DNS request will be made to the Domain Name System to obtain the IP address for the domain viki.com.
3. The packaged-up HTTP request then goes over the Internet to the server with the matching IP address. 
4. The remote server handles the request and sends a response over the internet back to my network interface which sends it to my browser, Chrome.
5. Lastly, Chrome displays the response in the form of a web page.


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