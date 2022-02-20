WHAT TO FOCUS ON
1. Build a general picture of the network infrastructure
- Protocols & network devices (e.g., networked devices, cables, wires, and radio waves)

2. Be aware of the limitations of the physical network
- TCP and HTTP rely on the underlying network and are therefore bound to its limitations like latency and bandwith.
Overcoming these limitations depends on how we the developers implement higher-level protocols (TCP, HTTP, etc) within our applications. 

3. Understand the protocols are systems of rules

4. Learn that IP enables communication between devices
- Make sure to form a clear mental model of what it does.



# What is the Internet?
A network of networks. It enables the communication of various networked applications--the interaction of multiple different protocols.

**Network:** Connected devices that can exchange data.

**W/LAN ((Wireless) Local Area Network):** Multiple devices connected wirelessly in the case of WLAN or via network cables in the case of LAM, to a network bridging device (i.e. a switch or hub). The switch/hub that connects these devices has geographical limitations so these devices must be located in the same place (e.g. an office building or school campus)

**Routers:** Network devices that can route data from one network to another network. Between each sub-network are systems of routers that direct the network traffic.

**Protcols:** A system of rules that govern the exchange/transmission of data.
There are lots of different protocols for 2 main reasons:
1. Diff. protocols address *different* aspects of network communication (e.g. HTTP protocol is for structuring messages and TCP is for transferring messages btwn apps)

2. Diff. protocols address the *same* aspect of network communication but in different ways or for a special use-case (e.g. both TCP and UDP are protocols for transferring messages btwn apps but do it in different ways)


# A Layered System
Breaking down network communication into modules and structuring those modules in a layered system helps us better understand the protocols in each layer since they're grouped by the aspect they address.

2 popular models that demo this layered system concept are:
1. The OSI Model (Open Systems Interconnection)
Layers are based on the function each one provides (e.g., physical addressing, logical addressing & routing, encryption, compression, etc.)
AND
2. TCP/IP model (Transfer Control Protocol / Internet Protocol model aka 'IP Suit' or 'DoD model')
Layers are based on the scope of communications within each layer (e.g., within a local network, btwn. networks, etc.)

LAYERS (there's overlap, so layers don't match up evenly)
| OSI model    | TCP/IP model |
| -------------| :-----------:|
| Application  | Application  |
| Presentation |      "       |
| Session      |      "       |
| Transport    | Transport    |
| Network      | Internet     |
| Data Link    | Link         |
| Physical     |      "       |


Data Encapsulation in network models is hiding data from one layer by encapsulating it within a data unit or PDU (**Protocol Data Unit**) of the layer below it.

PDUs are blocks of data transferred over a network, and are made up of the following:
1. A **header** (and sometimes a **footer/trailer**) that consists of protocol-specific metadata about itself.
2. A **Data Payload** that contains the data we want transferred over the network using a specific protocol at a particular network layer. It goes by different names depending on the layer and/or protocol, for example, it's called a **frame** at the 'Data Link / Link' layer, a **packet** at the 'Network / Internet' layer and a **segment** or **datagram** at the 'Transport' layer (which one depends on the protocol use).

The separation of layers adds a level of abstraction. A lower layer isn't concerned with how a protocol at another layer is implemented. It only needs to encapsulate *some data* from the layer above and provide the result of this encapsulation to the layer below.


#### 2 main characteristics of a physical network
##### Latency
The time it takes data to get from one point in a network to another point in a network. It's essentially a mesaure of delay, usually in milliseconds (ms).

There are 4 types of delay that constribute to the overall latency of a network connection:
1. **Propagation delay:** calculated as a ratio btwn. distance & speed, it's the time it takes for a message to go from sender to receiver
2. **Transmission delay:** the time it takes to push data onto a link (wires & cables) interconnected by switches, routers, and other network devices.
3. **Processing delay:** the time it takes data to be processed at every link (data doesn't directly cross from one line to another)
4. **Queuing delay:** the time it takes data to queue/buffer. This occurs when there's more data than a network device can process at one time, the data awaiting processing gets but in a queue/buffer.

##### Bandwidth
The amount of data that can be sent in a particular amount of time (usually a second).
Increasing bandwidth doesn't necessarily mean a decrease in latency.


# The Data Link / Link Layer
**What happens at this layer?**
It's an interface between the workings of the physical network and the more logical layers above.

**Primary function of protocols at this layer?**
Being able to identify devices and move data from one device to another on the physical network.

**What common protocol is used at this layer?**
The Ethernet Protocol, it has 2 important aspects; framing and addressing.

1. Ethernet Frames
A PDU that encapsulates data from the *Internet/Network* layer.

**Source & Destination MAC Address**, addresses of the device that created the frame and of the device the data is intended for.

**Data Payload**, contains data for the entire PDU from the layer above (e.g. an IP Packet)

**Interframe Gap (IFG)**, specified by the Ethernet protocol and varying in length based on the capability of the Ethernet connection, it's the brief pause between the transmission of each frame, allowing the receiver to prepare to receive the next frame. It contributes to the **Transmission delay** element of latency.

AND

2. MAC Addresses (aka 'physical address', 'burned in address')
A unique sequence of six 2-digit hexadecimal numbers assigned to a **network-enabled device** when it's manufactured.

2 important characteristics make MAC Addresses unscalable though:
* Addresses are physical not logical and
* Addresses are flat rather then hierarchical; they're a single sequence of values and can't be broken down into sub-divisions


# The Network / Internet Layer
**What happens at this layer?**
Inter-network communication

**Primary function of protocols at this layer?**
Facilitating communication btwn. hosts (e.g. computers) on different networks.

**What are the most common protocols at this layer?**
Internet Protocol (IP); IPv4 & IPv6 are currently in use. Although there are differences, 2 primary features that are the same are:

1. Encapsulation of data into packets
IP PDU's are called packets. The data payload here is the TCP segment or UDP datagram. The header made up of logic fields (i.e. there's a logical separation of the bits into fields determined by length of bits and order). These logic fields contain metadata used for transporting the packet.

Important fields include
**Checksum:** This is an error checking value generated via an algorithm. The destination device generates a value using the same algorithm and if it doesn't match, it drops the packet. IP doesn't manage retransmission of dropped packets. This is left to the layers above to implement.
**Source address:** The 32-bit IP address of the source (sender) of the packet
**Destination address:** The 32-bit IP address of the destination (intended recipient) of the packet

2. Routing capability via IP addressing
IP addresses are n-bits in length and divided into sections of bits that get converted from binary to decimal.
These addresses get assigned to devices when they join a network and fall within a range of addresses available to the LAN that the device is connected to.

The overall network is hierarchical and split into a logical subnetwork with each subnetwork defined by a range of IP addresses.

IPv6 uses more bits in its addresses and was created to expand the pool of addresses because IPv4 addresses will eventually be depleted. Compared to IPv4, IPv6 has a different structure to the address (mentioned above) and the header. There's also no error checking, IPv6 leaves that to the Link Layer Checksum.