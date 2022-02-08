# The Transport Layer
### Communication between processes
Concept of the internet as a *layered system* of communication where each layer provides a level of functionality or service to the layer above.

Re: network communication, what's happening at the Transport layer?
1. A direct connection between networked applications is established (aka end-to-end communication)
  - between an application running on one host and an application running on another host
  - between 2 different applications or processes running on the same host
2. The level of network reliability is established at this layer

* What protocol(s) is used at the Transport layer?
TCP or UDP

### Multiplexing and Demultiplexing
**Channels**, distinct lines of communication on a host machine for different applications and/or processes allowing them to send/receive data simultaneously.

Although we have multiple communication channels on a host, w/ IP addresses there's only one channel btwn hosts. A way to transmit multiple data inputs over a single host-to-host channel and then somehow separate them out at the other end is needed

**multiplexing**, breaking down & transmitting multiple signals over a single channel
**demultiplexing**, the putting together of multiple transmitted signals

Multiplexing and demultiplexing occurs thru the use of **network ports**

### Ports
An identifier for a specific process running on a host. This identifier is an integer in the range 0-65535.
Sections of the range are reserved for specific purposes. 

'Services running on servers'? may have a port in the well-known range assigned to them. If connecting via HTTP to a web-server running on a host machine, that web-server process will likely have port 80 assigned to it.

A service running on a client machine, e.g., a browser running on your laptop, won't use one of these well-known ports, but instead have an *ephemeral* or temporary port assigned to it by the operating system, for example 59258.

Source and destination port #s are included in the PDU for the transport layer. The name, and exact structure, of these PDUs varies by protocol, but they both include these two pieces of info

Data from the application layer is encapsulated as the data payload in this PDU, and the *source and destination port numbers within the PDU can be used to direct that data to specific processes on a host*. 

The entire PDU is then encapsulated as the data payload in an IP packet. *The IP addresses in the packet header can be used to direct data from one host to another*. The IP address and the port number *together* are what enables **end-to-end communication** btwn specific applications on different machines. The combination of IP address and port # info can be thought of as defining a **communication end-point** or more commonly, a **socket**. 

For now, think of sockets as the combination of IP address and port number, for example 216.3.128.12:8080.

### Sockets
THERE'S A DISTINCTION BTWN THE CONCEPT OF A NETWORK SOCKET VS. ITS IMPLMENTATION IN CODE
Conceptually, a socket is a communication end-point defined by an address-port pair. 
Implementation-wise it involves instantiating *socket* objects.

The idea of instantiating socket objects is needed to understand the difference btwn. *connection-oriented* and *connectionless* communication. The diff. btwn. these communication modes is important in understanding the differences btwn. the TCP and UDP protocols.

### Sockets and Connections
By instantiating multiple socket objects, we can implement **connection-oriented** network communication btwn. applications.

In a **connectionless system** we have one socket object defined by the IP address of the host machine and the port assigned to a particular process running on that machine. That object could call a listen() method which would allow it to wait for incoming messages intended for that specific ip/port pair. Messages could potentially come from any source, at any time, and in any order, but that isn't a concern in a connectionless system -- it would simply process any incoming messages as they arrived and send any responses as necessary.

A **connection-oriented system** has a socket object defined by the host IP and process port, just as in the connectionless system, also using a listen() method to wait for incoming messages; the difference in implementation is what happens when a message arrives. At this point a new socket object is instantiated; this new socket object isn't just defined by the local IP and port #, but also the IP and port of the process/host that sent the message. This new socket object then only listens for messages where all four pieces of info matched (source port, source IP, destination port, destination IP). The combination of these four pieces of information are commonly referred to as **a four-tuple**.

Any messages not matching this four-tuple would still be picked up by the original socket, which would then instantiate another socket object for the new connection.

A connection-oriented system creates a *dedicated virtual connection* for communication between a specific process running on one host and a specific process running on another host. The advantage of having a dedicated connection is that it more easily allows you to put in place rules for managing the communication such as the order of messages, acknowledgements that messages had been received, retransmission of messages that weren't received, and so on. The purpose of these types of additional communication rules is to **add more reliability to the communication**.

### Network Reliability
The protocols used in the lower layers of network communication, the Ethernet and Internet Protocols are inherently unreliable because when the checksum data finds that data has been corrupted along its journey, that data (i.e. the frame and packet) is dropped or simply discarded. Their protocols don't include a way to replace the lost data.

The possibility of losing data and not being able to replace it means the network from Ethernet up to--and including-- Internet is an *unreliable communication channel*

How can we transfer data reliably over an unreliable channel? We need a protocol that ensures all data that is sent is received at the other end and in the correct order.

#### Building a Reliable Protocol
Starting with the original issue and addressing new issues that arose with each solution, finally

Version 3 covered the fundamental elements required for reliable data transfer:

* In order delivery: data is received in the order that it was sent
* Error detection: corrupt data is identified using a checksum
* Handling data loss: missing data is retransmitted based on acknowledgements and timeouts
* Handling duplication: duplicate data is eliminated through the use of sequence numbers

Major flaw is that it's not efficient b/c data is one sent one piece at a time only after an ack is rec'd. This protocol is known as a **Stop-and-Wait** protocol. Spending a lot of time waiting for an ack isn't an efficient use of bandwidth.

#### Piplining for Performance
**Pipelining** an approach just like our protocol above except instead of one, multiple messages are sent at once. The network is still reliable because we're still receiving acks and retransmitting to handle data loss.

Various ways to implement pipelining; Go-back-N or Selective Repeat. Implementation isn't important, as both ways incorporate a *window* that represents the # of messages that can be sent through the pipeline at any one time. Once the right amount of ack are received the window moves on.

### Transmission Control Protocol (TCP)
One of the key characteristics of this protocol is the fact that it provides reliable data transfer.

The services that TCP provides makes it the protocol of choice for many networked applications. 
The flip-side though is the performance challenges that come with its complexity. 

TCP does attempt to balance this impact on performance by providing mechanisms for flow control and congestion avoidance.

Reliability isn't the only thing that TCP provides. It also provides data encapsulation and multiplexing through the use of TCP Segments.

#### TCP Segments
A TCP PDU is called a **segment**. Again, using a combination of headers & a payload encapsulation is provided to the data from the layer above.

Segment Header contains
* Source & Destination Port, which provide the multiplexing functionality of the protocol
* Other fields are related to the way that TCP implements reliable data transfer

Other important header fields:
* CHECKSUM: Provides the Error Detection aspect of TCP reliability. It is an error checking value generated by the sender using an algorithm. The receiver generates a value using the same algorithm and if it doesn't match, it drops the Segment. Having a Checksum at the Transport Layer does render Checksums at lower layers redundant to a certain extent. IPv6 headers don't include a Checksum for this reason, based on the assumption that checksums are implemented at either the Transport or Link/ Data Link layers (or both).

* SEQUENCE # and ACKNOWLEDGEMENT #: these two fields are used together to provide for the other elements of TCP reliability such as In-order Delivery, Handling Data Loss, and Handling Duplication. Don't need to learn the precice way TCP uses these fields to achieve this, beyond our scope.

* WINDOW SIZE field is related to Flow Control

* The Flag fields are one-bit boolean fields.
* - URG and PSH, are related to how the data contained in the Segment should be treated in terms of its importance or urgency, which is beyond our scope 
* - SYN, ACK, FIN, and RST flags are used to establish and end a TCP connection, as well as manage the state of that connection

#### TCP Connections
TCP is a connection-oriented protocol, it doesn't start sending application data until a connection has been established between application processes. 

In order to establish a connection, TCP uses what is known as a **Three-way Handshake** this is where the `SYN` and `ACK` flags come into play. The `FIN` flag is used in a different process, the **Four-way Handshake**, used for terminating connections.

A simplified version of the Three-Way Handshake:

* The sender sends a `SYN` message (a TCP Segment with the `SYN` flag set to 1)
* Upon receiving this `SYN` message, the receiver sends back a `SYN` `ACK` message (a TCP Segment with the `SYN` and `ACK` flags set to 1)
* Upon receiving the `SYN` `ACK`, the sender then sends an `ACK` (a TCP Segment with the `ACK` flag set to 1)

Once the `ACK` message is sent, the sender can immediately start sending application data. The receiver has to wait until it receives the `ACK` before it can send any data back to the sender. One of the main reasons for this process is to synchronise (`SYN`) the sequence #s that'll be used during the connection.

Part of the purpose of the flags is to manage the connection state. Most of the time the state we're most concerned with is ESTABLISHED, and also LISTEN on the server side. The other states are related to the establishment and termination of connections.

The process for establishing a TCP connection.

In the initial establishment of a connection, a key characteristic of the process is that the sender can't send any application data until after it has sent the `ACK` Segment. There's an entire round-trip of latency before any application data can be exchanged. This hand-shake process occurs every time a TCP connection is made, which clearly has an impact on any application which uses TCP at the transport layer.


#### Flow Control
In order to help facilitate efficient data transfer once a connection is established, TCP provides mechanisms for **flow control** and congestion avoidance.

A mechanism to prevent the sender from overwhelming the receiver with too much data at once.

Data awaiting processing is stored in a 'buffer'. Each side of a connection can let the other side know the amount of data that it is willing to accept via the `WINDOW` field of the TCP header. **This number is dynamic, and can change during the course of a connection**. If the receiver's buffer is getting full it can set a lower amount in the `WINDOW` field of a Segment it sends to the sender, the sender can then reduce the amount of data it sends accordingly.

Although flow control prevents the sender from overwhelming the receiver, it doesn't prevent either the sender or receiver from overwhelming the underlying network. For that task we need a different mechanism: Congestion Avoidance.

#### Congestion Avoidance
In order to help facilitate efficient data transfer once a connection is established, TCP provides mechanisms for flow control and **congestion avoidance**.

Network Congestion is a situation that occurs when there is more data being transmitted on the network than there is network capacity to process and transmit the data.

A mechanism to prevent either the sender or receiver from overwhelming the underlying network

IP packets moving across networks in a series of 'hops'. At each hop, the packet needs to be processed: the router at that hop runs a `checksum` on the packet data; it also needs to check the destination address and work out how to route the packet to the next hop on its journey to that destination. All of this processing takes time, and a router can only process so much data at once. Routers use a 'buffer' to store data that is awaiting processing, but if there is more data to be processed than can fit in the buffer, the buffer over-flows and those data packets are dropped.

TCP actually uses data loss as a feedback mechanism to detect, and avoid, network congestion; if lots of retransmissions are occurring, TCP takes this as a sign that the network is congested and reduces the size of the transmission window.

There are various different approaches and algorithms for determining the size of the initial transmission window, and how much it should be reduced or increased by depending on network conditions. The exact algorithm or approach used will depend on which variant of TCP is in operation.

#### Disadvantages of TCP
* There's a latency overhead in establishing a TCP connection due to the handshake process. 
* Another potential issue with using TCP is **Head-of-Line (HOL) blocking**.

Head-of-line blocking is a general networking concept, not specific to TCP. In general terms it relates to how issues in delivering or processing one message in a sequence of messages can delay or 'block' the delivery or processing of the subsequent messages in the sequence.

With TCP, HOL blocking can occur as a result of TCP's in-order delivery of segments. If one of the segments goes missing and needs to be retransmitted, the segments that come after it in the sequence can't be processed, and need to be buffered until the retransmission has occurred. This can lead to increased queuing delay which, as we saw in an earlier assignment, is one of the elements of latency.

### User Datagram Protocol (UDP)
UDP doesn't implement reliable data transmission thru sequencing or retransmitting lost data, nor does it transport data efficiently using flow control and congestion avoidance. 

A UDP's PDU is called a Datagram and is very simple. It encapsulates the PDU from the layer above into it's data payload and the header only has 4 fields; 
- source & destination port #s, multiplexing is possible just like with TCP
- length, the length, in bits, of the Datagram, including any encapsulated data
- checksum, to provide error detection**

**optional is using IPv4, but needed if using IPv6 since IPv6 packets don't include checksums

UDP doesn't resolve the inherent unreliability of the layers below it (i.e. the Data Link & Network layers)

* UDP provides no guarantee of message delivery
* UDP provides no guarantee of message delivery order
* UDP provides no built-in congestion avoidance or flow-control mechanisms
* UDP provides no connection state tracking, since it is a connectionless protocol

#### The Case for UDP
The advantage that UDP has over TCP is its simplicity, which provides two things speed and flexibility.

**Re: speed**
UDP is a connectionless protocol, therefore, applications using UDP at the Transport layer can send data w/o waiting for a connection to be established w/ the application process of the receiver. 
The lack of acknowledgements and retransmissions means the actual data delivery is faster; once a datagram is sent it doesn't have to be sent again. 
Latency is less of an issue since without acknowledgements data essentially just flows one way: from sender to receiver. 

The lack of in-order delivery also removes the issue of Head-of-line blocking (at least at the Transport layer).
