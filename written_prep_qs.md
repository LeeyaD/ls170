# The Internet
* What is a network? - ADDED
Two or more connected devices that can share data.


* What is a local area network (LAN)? - ADDED
A group of hosts connected together in one physical location.
**key thing is the geographic


* What is a hub and what is it used for? - ADDED
A network device that is essentially a multi-port repeater facilitating communication within a network. When it receives communication from one host, it duplicates it and sends it to all other connected hosts.


* What is a switch and what is it used for? - ADDED
A network device that facilitates communication within a network.


* What is a router and what is it used for? - ADDED
A network device that facilitates communication between networks.


* What is a protocol? - ADDED
A systems of rules.


* What are network protocols? - ADDED
Systems of rules that control the transmission of data over a network.


* What makes up a network's infrastructure? (high-level picture) - ADDED
Tangible network devices that facilitate network communication; i.e., routers, switches, cables, etc.


* Why are there different types of protocols? - ADDED
Because there are different types of protocols that deal with different areas of network communication (e.g., HTTP for structuring messages and TCP for transferring messages btwn. apps) and others that deal with the same areas of network communication but in a different way (e.g., TCP and UDP both transfer messages btwn. apps but they do it in different ways).


* What is the internet? <<--- ADDED
A network of networks. It's made up of a *network infrastructure* (i.e. routers, switches, cables, etc.) and *protocols* that support it. It's the interaction of those protocols via the infrastructure that facilitates the communication of networked applications.


* What are network 'Hops'? - ADDED
When data is transmitted across multiple routers to get to the target host. Each 'hop' is data being transmitted from one link to another.


* What are the characteristics/limitations of the physical network? - ADDED
Latency and bandwidth. 


* What is *latency*? - ADDED
A measure of delay, it's the time it takes for data to travel from one point in a network to another. There are 4 types of delays that contirbute to the overall latency of a network: 
1. Propagation delay: which is what we think of when imagine latency, it's the time it takes for data to go from one point to another.
2. Transmission delay: the time it takes to push data onto a link (i.e. the many diff. wires & cables).
3. Processing delay: the time it takes data to be processed at every link since data doesn't directly cross from one line to another.
4. Queuing delay: the time it takes data to queue/buffer, which occurs when there's more data being transmitted than a network device can processed at one time.


* What is the relationship between network 'Hops' and latency?
Each 'hop' can increase latency thanks to *processing* and *transmission* delays, that is the time it takes data to be processed at and pushed onto a link (network wire/cable), repsectively.


* What is *bandwidth*?
A measure of capacity, it's the amount of data that can be sent over a network connection in a set period of time.


* In the context of network protocols, what is *encapsulation*?
It's when data from one one layer is being hid in the PDU, specifically the data payload, of the layer below it. 


* Why is data encapsulation important?
It provides a level of abstraction, implementing data encapsulation thru PDUs creates separation between protocols operating at different network layers. It allows them to work together without being concerned about each others' implementation.


* What are well-known models that demonstrate network communication as a layered system? and what are their layers?
The OSI and TCP/IP models breakdown network communication into layers where protocols are grouped by what they address. The OSI model groups protocols by the function they provide and has 7 layers; physical, data link, network, transport, session, presentation, and application. Meanwhile the TCP/IP (IP Suite) model groups protocols by the scope of communication within the layer and has 4 layers; link, internet, transport, and application.


* What is the purpose of having models like OSI and TCP/IP?
They provide an easy to understand overview of how the internet works as a whole by modularize different levels of responsibility within that system. It helps developers develop a clear idea of how a particular protocol works and how to use it at the implementation level.


* What is a PDU? and what are its parts?
It's a block of code being transmitted over a network. It consists of a header, a data payload and sometimes a trailer or footer.


* What is a Header / Footer/Trailer?
Part of a protocol's PDU, they contain protocol-specific metadata about the PDU.


* What is Data Payload?
Encapsulated data that we want to transport using a specific protocol at a particular layer. An Ethernet PDU is called a frame, an IP PDU is called a 'packet' and a TCP or UDP PDU is, respectively, called a 'segment' or 'datagram'.


* Why are PDUs important?
They're how data encapsulation is implemented. The entire PDU from a protocol at one layer is set as the data payload for a protocol one layer below. 


* What is the relationship between PDU and Data Payload?
One gets encapsulated into the other, the entire PDU of a protocol at one layer is encapsulated into the data payload of the protocol one layer below.


* Give an overview of the physical layer
The physical layer is where the electrical signals, light, and radio waves, which carry network communications, are being transmitted across wires, cables, and wifi.


* Give an overview of the Data Link/Link layer - BURNING Q
It's the interface between the physical network and the more logical layers above. 


* What is the Ethernet Protocol?
A system of rules that controls physical point-to-point communication between devices within a network.


* What service does the Ethernet Protocol provide?
It enables communication between devices within a network via MAC addressing and *frames*.


* What are the Ethernet protocol's primary functions?
  1. Identifying devices connected to a local network thru their MAC addresses and
  2. Moving data over the physical network btwn. the devices that make it up (i.e., hosts, switches, routers) thru the use of *frames* (i.e., the Ethernet PDU)


* What is a MAC address and what is its role in network communication?
It's a sequence of six two-digit hexadecimal numbers that is (usually) permanently associated with a particular device and, therefore, sometimes referred to as a physical address. Re: network communication, since the MAC address is used to identify devices on a local network it facilitates physical point-to-point communication.


* Why are MAC addresses unscalable?
The addresses are physical and there's no logical hierarchy, the entire address is a one sequence of values that can't be broken down into sub-divisions. 

If you were to travel to other states and connect to different LANs, each of those network devices would need a record of *your* device's MAC address in order to transmit data. Add to this, the additional need for records to be kept for everyone else's devices and it's just impossible; and we're not even talking internationally!


* What is included in an Ethernet frame?
A header containing, among other fields, the source and destination MAC Addresses and a data payload containing an IP packet (i.e., the Internet Protocol Data Unit).


* Give an overview of the the Network/Internet layer and it's role
This layer make inter-network communication between devices possible thru the use of IP Addressing and *packets*. This communication is between devices, not specific applications running on those devices.


* What is the Internet Protocol?
A system of rules that control the transmission of data between devices from different networks. It accomplishes this by encapsulating data from the transport layer (e.g. a TCP segment or UDP datagram) into the data payload of its PDU, called a *packet*. This packet is then routed to a device on another network through IP addressing.
Note: There are two versions of IP currently in use: IPv4 and IPv6.
 

* Which of the following statements are true in relation to the Internet Protocol?
Subnetting is actually *enabled* by IP addressing rather than being an alternative to it. It is the hierarchical structure of IP Addresses that allows networks to be logically split into subnets.


* What is an IP address?
It's a unique address assigned to devices as they join a local network, and is used to locate these devices on the internet. These addresses are 32-bits in length, divided into 4 sets of numbers and is what allows networks to be split into logical subnets.

The overall network is hierarchical and split into subnetworks or subnets, each subnet is defined by a range of IP addresses available to it. And so, IP addresses function like a postal address with each section of it mapping to a specific part of the internet. The first two sets of numbers usually reference the network and sub-network, much like the city and state do in a postal address. The third is the host, and the fourth part references a machine connected to that host (like the town/county and street address).

The breakdown of can IP address into 4 sections is the standard for IPv4.

IPv6 uses 128-bit addresses (divided into eight 16-bit blocks) and was created to expand the pool of addresses as IPv4 addresses will eventually be depleted.

- There is also a new standard for IP addresses which is in the process of being adopted, IPv6. This representation of an IP address is broken into 8 sets of hexadecimal characters. The first 4 sets are used to locate a specific network on the internet. The last 4 sets are typically used to identify a particular interface or device within that network.

* What's included in an IP packet?
A header containing, among other fields, the source and destination IP Addresses and a data payload containing a TCP segment or UDP datagram (i.e., the Tranmission Control or User Datagram Protocol Data Unit).


* What is a packet in computer networking?
* Why do we need both MAC addresses and IP addresses?

* Explain How lower-level protocols work in general?


* What service does the [?] Protocol provide?
* What is included in an [protocol] [PDU name]?

# The Transport Layer
* Give an overview of the Transport layer
Transport: end-to-end communication between devices
Transport: end-to-end communication between networked applications; 2 important things it does is 
1. Establishing a connection between networked applications
2. Breaking down data from the application layer into segments/datagrams
2. Breaking down data from the application layer into segments/datagrams
Replying on network ports to put the segment/datagram pieces together and directs

* What is a port number?
* What is a network port number?


* What are (network) ports?
A port is an identifier for a specific process or application running on a host.
Ports are used in the process of multiplexing and demultiplexing.
Source and destination port numbers are listed in Transport layer PDUs.


* What are multiplexing and demultiplexing?
Multiplexing and demultiplexing provides the ability to transmit *multiple signals over a single channel*.
* Multiplexing is enabled through the use of *network ports*


* How do port numbers and IP addresses work together?


* What is a network socket?
At a conceptual level it can mean the combination of IP address and port number that provides a communication end-point.

At an implementation level it can refer to a socket object used to create connections between applications.


49. **How do sockets on the implementation level relate to the idea of protocols being connectionless or connection-oriented?** 


* How do transport layer protocols enable communication between processes?


* What is network reliability?
* The underlying network is *inherently unreliable*. If we want reliable data transport we need to implement a system of rules to enable it.


* What are the fundamental elements of reliable protocol?
* What does it mean that network reliability is engineered?


41. **What is a checksum and what is it used for? How is it used?**


* What is a three-way handshake? What is it used for?
To establish a TCP connection between two different applications.


* What are the advantages and disadvantages of a Three-way handshake?


* What is network congestion?


* What is Congestion Avoidance?
Congestion avoidance is a process by which TCP uses data loss (based on the volume of retransmissions required) as a feedback mechanism to determine how congested the network is, and adjusts the amount of data being sent accordingly.


* What is Flow Control? How does it work and why do we need it?
Flow Control is a mechanism to prevent the sender overwhelming the receiver with more data than it can process. Each participant in a connection lets the other participant know how much data it is willing to accept using the WINDOW field in the TCP header.


* What is pipelining protocols? What are the benefits of it?

48. **Is TCP connectionless? Why?**
51. **What does it mean that the protocol is connection-oriented?**

55. **How does TCP facilitate efficient data transfer?**


* What are the benefits & trade-offs of TCP?
-TCP is a *connection-oriented* protocol. It establishes a connection using the *Three-way-handshake*
* TCP provides reliability through message *acknowledgement* and *retransmission*, and *in-order delivery*.
* TCP also provides *Flow Control* and *Congestion Avoidance*
* The main *downsides of TCP* are the *latency overhead of establishing a connection*, and the potential *Head-of-line blocking* as a result of in-order delivery.
TCP is a connection-oriented protocol
TCP provides multiplexing and demultiplexing
TCP provides in-order delivery <--RELIABILITY>
TCP provides de-duplication
TCP provides message acknowledgement and retransmission <--RELIABILITY>
TCP provides error detection


* What are the benefits & trade-offs of UDP?
* UDP is a very simple protocol compared to TCP. It provides *multiplexing*, but no reliability, no in-order delivery, and no congestion or flow control.
* UDP is *connectionless*, and so doesn't need to establish a connection before it starts sending data
* Although it is unreliable, the *advantage of UDP* is *speed* and *flexibility*.
UDP is a connectionless protocol
UDP provides multiplexing and demultiplexing
UDP provides error detection
- UDP does provide error detection via a checksum, though this is optional if using IPv4.
UDP doesn't provide in-order delivery
UDP doesn't provide de-duplication
UDP doesn't provide message acknowledgement and retransmission
------------------------------------------------------------------------------------




3. **Is the Internet the same thing as a network?** 
4. **What is WEB (world wide web)**
10. **What does it mean that a protocol is stateless?**
5. **What is the difference between network, Internet, and WEB?**
39. **What is DNS and how does it work?**
**How can we as developers deals with the limitations of physical network?**
 



* Give an overview of the Application layer
Application: end-to-end communication between applications

63. **Give an overview of the Application Layer.** 
64. **What is HTML?**
65. **What is a URL and what components does it have?**
66. **What is a Query string? What it is used for?**
67. **What URL encoding is and when it might be used for?**
68. **Which characters have to be encoded in the URL? Why?**
69. **What is www in the URL?** 
70. **What is URI?**
71. **What is the difference between scheme and protocol in URL?**
72. **What is HTTP?**
73. **What is the role of HTTP?**
74. **Explain the client-server model of web interactions, and the role of HTTP as a protocol within that model**
75. **What are HTTP requests and responses? What are the components of each?**
76. **Describe the HTTP request/response cycle.**
77. **What is a** s**tate in the context of the 'web'?**
78. **What is** s**tatelessness?**
79. **What is a stateful Web Application?**
80. **How can we mimic a stateful application?**
81. **What is the difference between stateful and stateless applications?**
82. **What does it mean that HTTP is a 'stateless protocol?** 
83. **Why HTTP makes it difficult to build a stateful application?**
84. **How the idea that HTTP is a stateless protocol makes the web difficult to secure?** 
85. **What is a `GET` request and how does it work?** 
86. **How is `GET` request initiated?**
87. **What is the HTTP response body and what do we use it for?**
88. **What are the obligatory components of HTTP requests?** 
89. **What are the obligatory components of HTTP response?**
90. **Which HTTP method would you use to send sensitive information to a server? Why?**
91. **Compare `GET` and `POST` methods.**
92. **Describe how would you send a `GET` request to a server and what would happen at each stage.**
93. **Describe how would you send `POST` requests to a server and what is happening at each stage.**
94. **What is a status code? What are some of the status codes types? What is the purpose of status codes?** 
95. **Imagine you are using an HTTP tool and you received a status code `302`. What does this status code mean and what happens if you receive a status code like that?** 
96. **How do modern web applications 'remember' state for each client?**
97. **What role does AJAX play in displaying dynamic content in web applications?**
98. **Describe some of the security threats and what can be done to minimize them?**
99. **What is the Same Origin Policy? How it is used to mitigate certain security threats?**  
100. **What determines whether a request should use `GET` or `POST` as its HTTP method?**
101. **What is the relationship between a scheme and a protocol in the context of a URL?**
102. **In what ways can we pass information to the application server via the URL?**
103. **How insecure HTTP message transfer looks like?**
104. **What services does HTTP provide and what are the particular problems each of them aims to address?**
105. **What is TLS Handshake?**
106. **What is symmetric key encryption? What is it used for?**
107. **What is asymmetric key encryption? What is it used for?**
108. **Describe SSL/TLS encryption process.**
109. **Describe the pros and cons of TLS Handshake**
110. **Why do we need digital TLS/SSL certificates?** 
111. **What is it CA hierarchy and what is its role in providing secure message transfer?**
112. **What is Cipher Suites and what do we need it for?**
113. **How does TLS add a security layer to HTTP?**
114. **Compare HTTP and HTTPS.**
115. **Does HTTPS use other protocols?** 
116. **How do you know a website uses HTTPS?**
117. **Give examples of some protocols that would be used when a user interacts with a banking website. What would be the role of those protocols?** 
118. **What is server-side infrastructure? What are its basic components?**
119. **What is a server? What is its role?** 
120. **What are optimizations that developers can do in order to improve performance and minimize latency?**