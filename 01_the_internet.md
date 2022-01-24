# What is the Internet?
A network of networks. It enables the communication of various networked applications--the interaction of multiple different protocols.

**Network**
Devices connetected where they can communicate or exchange data.

### (Wireless)LAN [Local Area Network]
Multiple computers/devices connected (wirelessly or w/ network cables), to a network bridging device (i.e. a switch or hub). **Scope of communication is limited to devices that are connected to this switch/hub which has geographical limitations.**

### Routers
Network devices that allow communication between networks by routing network traffic to other networks. Act as a gateway into & out of a network. Between each sub-network are systems of routers that direct the network traffic.
        comp                           comp
          |                             |
comp - switch -- router --- router -- switch - comp
          |                             |
        comp                           comp


# Protcols
A system of rules that govern the exchange/transmission of data.

There are lots of different protocols for various reasons, but the 2 main reasons are:
1. Diff. protocols address *different* aspects of network communication (e.g. HTTP protocol for structuring messages and TCP is for transfering messages btwn apps)

2. Diff. protocols address the *same* aspect of network communication but in different ways or for a special use-case (e.g. both TCP and UDP are protocols for transferring messages btwn apps but do it in different ways)


# A Layered System
Network communication can be broken down into modules and structured in a layering system where protocols are grouped by the aspect they address.

2 popular models that demo this concept are:

1. The OSI Model (Open Systems Interconnection)
Layers are based on the function each one provides (e.g., physical addressing, logical addressing & routing, encryption, compression, etc.)

AND

2. TCP/IP model (Transfer Control Protocol, aka 'IP Suit' or DoD model)
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


Data Encapsulation in network models is when data is being hid from one layer by encapsulating it in the data unit or PDU (**Protocol Data Unit**)of the layer below it.

PDUs are blocks of data transferred over a network, and are made up of the following:
1. A **header** (and sometimes a **footer/trailer**) that consists of protocol-specific metadata about the PDU.
2. A **Data Payload** that contains the data being transferred over the network using a specific protocol at a particular network layer. It goes by different names depending on the layer, for example, it's called a **frame** at the 'Data Link / Link' layer, a **packet** at the 'Network / Internet' layer and a **segment** (**datagram** depending upon the protocol) at the 'Transport' layer in the TCP/IP model.

Data Payloads are instrumental in how data encapsulation is executed, the entire PDU (header & data payload) from a protocol at one layer is set as the data payload for a protocol at the layer below.

**Protocols at one layer provide services to the layer above

The separation of layers adds a level of abstraction in that a lower layer isn't concerned with how a protocol at another layer is implemented. It only needs to encapsulate *some data* from the layer above and provide the result of this encapsulation to the layer below.

# The Physical Network
Important networking concepts to keep in mind:
1. Protocols are a system of rules for network communication
2. Groups of protocols work in a layered system. Protocols at one layer provide services to the layer above.
3. Data is encapsulated in a PDU, creating a separation between protocols operating at different layers

The most basic level is the physical network (i.e. the networked devices, cables, wires, etc.). Physical laws & rules determine how data actually gets transported from one place to another. 

Real-word limitations & boundaries (e.g. how fast an electrical or light signal can travel or the distance a radio wave can reach) determine the physical characteristics of a network, which impact how protocols function.

#### Bits & Signals
Data here is a stream of bits without any logical structure.
Bits, binary data, gets converted into signals (electric, light, or radio waves) in order to be transported

#### 2 main characteristics of a physical network
##### Latency
The time it takes data to get from one point in a network to another point in a network. It's essentially a mesaure of delay, usually in milliseconds (ms).

There are 4 types of delay that constribute to the overall latency of a network connection:
1. **Propagation delay:** calculated as a ratio btwn. distance & speed, it's the time it takes for a message to go from sender to receiver
2. **Transmission delay:** the time it takes to push data onto a link (i.e. the many diff. wires & cables interconnected by switches, routers, and other network devices).
3. **Processing delay:** the time it takes data to be processed at every link (data doesn't directly cross from one line to another)
4. **Queuing delauy:** the time it takes data to queue/buffer. This occurs when there's more data than a network device can process at one time

Other important(?) terms:
**Last-mile latency:** when delays occur within parts of the network that are closest to the end pionts (e.g. getting the network signal from your ISP's network to your home/office).
**Round-Trip Time (RTT):** a latency calculation, it's the time for a signal to be send PLUS the time for an acknowledgment/response to be received.

##### Bandwidth
The amount of data that can be sent in a particular amount of time (usually a second).

The car traveling 50mph on a 10 mile journey and the addition of other cars demonstrated that increasing bandwidth doesn't automatically mean a decrease in latency. 

**Bandwidth bottleneck:** the point where bandwidth changes from relatively high to relatively low.


# The Data Link / Link Layer
**What happens at this layer?**
It's an interface between the workings of the physical network and the more logical layers above

**What kinds of protocols are at this layer?**
Ones mainly concerned with one of the most important rules for transferring data from one place to another--*identifying devices* on the physical network AND moving data over the physical betwork btwn. the devices that make it up; for example, hosts (e.g. computers), switches, routers.

**What are the most common protocols at this layer?**
The Ethernet Protocol, it has 2 important aspects; framing and addressing.

1. Ethernet Frames
A PDU that encapsulates data from the *Internet/Network* layer. It's the lowest level where encapsulation occurs.

Here logical structure is added to the binary data, defining which bits are the data payload and which are metadata to be used in the process of transporting the frame.

An Ethernet-compliant network device can identify the different parts of a frame by the different 'fields' of data (each has a specific length in bytes and appear in a set order).

**Source & Destination MAC Address**, addresses of the device that created the frame and of the device the data is intended for.

**Data Payload**, contains data for the entire PDU from the layer above (e.g. an IP Packet)

The two fields above exist across all the different Ethernet standards but different Ethernet versions have slightly different structures.

**Interframe Gap (IFG), specified by the Ethernet protocol and varying in length based on the capability of the Ethernet connection, it's the brief
pause between the transmission of each frame, allowing the receiver to prepare to receive the next frame. It contributes to the **Transmission delay** element of latency.

2. MAC Addresses (aka 'physical address', 'burned in address')
A unique sequence of six 2-digit hexadecimal numbers assigned to a **network-enabled device** (e.g. a Network Interface Card-NIC- found in PCs & laptops) when it's manufactured.

A hub sends the frame to every device on the network, the devices simply ignore the frame if the address don't match up.

A switch uses the destination address in order to direct a frame only to the intended device thru the use of a MAC Address Table; a record of the MAC addresses of the devices connected to it and their associated Ethernet port (where the device is connected on the switch).

2 important characteristics make MAC Addresses unscalable though:

* Addresses are physical not logical since each address is burned in/tied to a specific address
* Addresses are flat rather then hierarchical; the entire address is a single sequence of values and can't be broken down into sub-divisions


