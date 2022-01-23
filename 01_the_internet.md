# What is the Internet?
A network of networks that enable communication of various networked applications--the interaction of multiple different protocols (systems of rules).

**Network**
Devices connetected in such a way that they can communicate or exchange data.

### (Wireless)LAN [Local Area Network]
Multiple computers/devices connected (wirelessly or w/ network cables), to a network bridging device (i.e. a switch or hub). **The scope of communication is limited to devices that are connected to this switch/hub which has geographical limitations.

### Routers
Network devices that allow communication between networks by routing network traffic to other networks. Act as a gateway into & out of a network. Between each sub-network are systems of routers that direct the network traffic.
        comp                           comp
          |                             |
comp - switch -- router --- router -- switch - comp
          |                             |
        comp                           comp


# Protcols
A system of rules that govern the exchange/transmission of data

There are lots of different ones for various reasons, but the 2 main reasons are:
1. To address *different* aspects of network communication (e.g. HTTP protocol for structuring messages and TCP is for transfering messages btwn apps)

2. To address the *same* aspect of network communication but in different ways or for a special use-case (e.g. both TCP and UDP are protocols for transferring messages btwn apps but do it in different ways)

# A Layered System

