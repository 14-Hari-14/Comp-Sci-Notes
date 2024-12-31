

2024-10-27 16:08

Tags:

# CN_MOD_3

![[Pasted image 20241027160816.png]]

## Network Layer 

The network layer is responsible for the source to destination(end to end) delivery of a packet across networks. To achieve this the layer must know 
- Topology of the communication network (set of all routers)
- choose appropriate path for the data delivery 
- avoid overloading the network

### Duties of Network Layer
1. **Internetworking**
2. **Routing**
3. **Fragmenting**
4. **Logical Addressing**
5. **Packetizing**

### Types of services provided to the Upper Layer
1. **Connectionless Service**
2. **Connection Oriented Service**

### Types of SUBNET in Network Layer
1. **Virtual Circuit Network**
2. **Datagram Subnet**


## Network Layer Design Issues
1. Store and Forward Packet Switching
2. Services provided to the Transport Layer
3. Implementation of the connectionless service
4. Implementation of the connection oriented service
5. Comparison of the virtual circuit and datagram subnet


### Store And Forward Packet Switching

![[Store-Forward-Packet-Switching.png]]

Here the host H1 has a packet to send to H2 it sends it to the nearest router its connected to. The router stores it until the complete packet is received to perform checksum and then it sends it to the next router and so on and so forth until it reaches the host.

### Services Provided to the Transport Layer
Network Layer provides services to the Transport Layer at the network/transport layer interface.
The properties of the services provided are:
- Services should be independent of the router technology
- The transport layer should be shielded from the  topology, type and number of the routers present
- The network addresses made available to the Transport layer should have uniform numbering plan even across LAN and WAN's

To comply with these the goals the developers have 2 options to either opt for **connectionless services** or go for the **connection oriented services**

In connectionless service the host will manage the error and flow correction and the network will just have minimal features like **SEND/ RECEIVE PACKETS** so no connection is to be made. This makes the network simpler and more flexible

In connection oriented service the network should handle the connections since it results in increased **Quality of Service (QoS)**. This is needed for real time traffic such as audio and video which is becoming more necessary in today's internet.

Based on the service used the network layer will use different subnets to transmit data

### Implementation of the connectionless service

If **Connectionless service** is used the subnet used is **DATAGRAM SUBNET**. The packets are injected individually and routed independently of each other.

![[datagram-subnet.png]]

### Implementation of the connection oriented service
If **Connection oriented service** is used the subnet used is **Virtual Circuit**. The connection is formed first and then the packets are sent 
![[virtual-circuit-subnet.png]]



### Comparison between VC and datagram

| issues                   | connectionless                                        | connection-oriented                                          |
| ------------------------ | ----------------------------------------------------- | ------------------------------------------------------------ |
| circuit-setup            | not required                                          | required                                                     |
| addressing               | each packet has full source & destination address     | each packet contains a short VC number                       |
| State information        | Routers dont hold state information about connections | Each VC requires router table space per connection           |
| Routing                  | Independent for each packet                           | Route chosen when VC is set up all packets follow that route |
| Effect of router failure | None, except for packet lost during crash             | all VC's that pass through that failed router are terminated |
| QoS                      | Difficult                                             | Easy if enough resources are allocated in advance            |
| Congestion Control       | Difficult                                             | Easy if enough resources are allocated in advance            |



## Routing Algorithms
Part of the network layer that decides which output line will the incoming packet be transmitted on. 
- If the network uses datagram it must be calculated for each packet. 
- If it uses VC then it must be calculated on when a new VC is being set up.

The main functions performed are as follows:
- routing
- congestion control
- internetworking


**Routing:** The process of forwarding data packets so that it reaches its intended destination.
The main goals of Routing are:
- **Correctness**
- **Simplicity**
- **Robustness**
- **Stability**
- **Fairness**
- **Optimality**

## Classifications of Routing Algorithms are
-  **ADAPTIVE Routing Algorithm**: 
	- These algorithms change their routing decisions in response to change in the topology and traffic. 
	- They get the information from adjacent or all the routers connected in the network. The routing parameters are:
		- **Distance**
		- **No of Hops**
		- **Transit Time**


-  **NON ADAPTIVE Routing Algorithm**
	- These algorithms dont change their routing decisions in response to topology and traffic and instead the route is computed in advance, offline and downloaded to the routers when the network is booted. 
	- Its also known as a static routing


## Different Routing Algorithms
- **The Optimality Principle**
- **Shortest Path Routing** (djikstra's algo)
- **Flooding** (every packet sent to the node is sent to every other node except for itself)
- **Distance Vector Routing**
- **Link State Routing**
- **Multicast Routing**
- **Routing for Mobile Hosts**


### Flooding
![[flooding_routing.png]]

Packet going to A will send  packet to B, C, D
Packet going to B will send packet to C, E
Packet going to C will send packet to B, D, F
Packet going to D will send packet to C, F
Packet going to E will send packet to F
Packet going to F will send packet to E

To control redundancy use:
- **hop counter** 
- **sequence number** 
- **selective flooding**

#### Controlled Flooding
**HOP COUNTER**
when the packet is created its given a hop counter value whenever it passes through a router(hop) the value of the counter is decremented

Ideally its initialised to the value of length from the source to destination however if that distance isnt known the worst case scenario is used which is the complete diameter of the subnet

**SEQUENCE NUMBER**
The host gives a sequence number to the packet. Whenever the packet is received by router it checks if it has been received before(present in the seen list) if its not seen then it will forward the packet to every neighbour else if its seen then it will not forward 


**SELECTIVE FLOODING**
The packet is sent only to those lines which are going in approximately the correct direction

#### Uncontrolled Flooding
The incoming packets are sent to all neighbours

**Advantages**
- Highly Robust
- Set up route in VC
- Always chooses the shortest path
- Broadcast msg to all nodes

**Disadvantages**
- Costly in terms of network bandwidth
- duplicated msg in the network


### Distance Vector Routing
Each hop/router has a table where the least distance between the router and every other router and which line to use to get there is stored 
# References
---


	