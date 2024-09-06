
2024-08-11 21:49


Status: 

Tags:

# Module 1

## Basic Terminology

**Network:** Its the collection of autonomous computers connected by a single technology. Connection can be copper wire optical cables or wireless mediums like infra red waves

**Networking:**  Its the process of connecting 2 or more computing devices for exchange of information/resources

**Nodes:** Individual devices

**Bandwidth:** The rate of data transmission between 2 nodes 

## Uses of computer networks


**resource sharing:** group of office workers can share network to access a common resource like printer

**client-server model:** this is how the networks work the client sends a request to the server and waits the server after receiving the request  send the corresponding data back

![[client-server-diagram.png]]

**Application of client server model** 
- Home applications
	- Access to remote information
	- person to person communication
	- Online gaming
- Business Applications
	- e-commerce
	- e-mail
-  Mobile Users
	- mobile computing
	- wireless networks
- Social Issues
	- social media platforms
## Computer Network Components

Computer network components are the major parts required to install the software
**Examples:**
- **NIC (Network Interface Card)**
	- Wired 
	- Wireless
- **Hub**
- **Router**
- **Switch**
- **Modem**
- **Cables and Connectors**
- **Repeaters**
- **Gateway**
- **Bridge**

### NIC

- Its also called as the network interface card. It is used to connect one computer to another on a network 
- Transfer Rate: 10, 100, 1000 Mb/s
- The MAC address of the device is physically encoded into the chip so that we can uniquely identify the network card . The **MAC address** is stored in the **PROM**.
	- **PS:** since the mac address is stored on the PROM and in some cases the EPROM we can solder new MAC address on the NIC to permanently change the address 
	- To make a temporary change the software mac address takes precedence and can be modified using code
	- [Read more about this here](https://www.quora.com/Is-it-possible-to-change-a-MAC-address-permanently)
- Types of NIC: 
	- **Wired:** It's present inside the motherboard cables and connectors are used to transfer data in wired NIC
	- **Wireless:** Contains antenna to obtain the connection over the wired networks

are layer 3 devices that enable communication across networks by routing packets between those devices based on IP addresses. (Routing, I
### HUB
**Definition:** Its a hardware device that divides the network connection among multiple devices.

**Working:** 
One computer will send request to the hub. The hub will then take the request and send it over to the network and each node on the network will check if the request is related to them. If no node is found then the request is dropped. 

**Disadvantages:**
This process uses a lot of bandwidth and limits the communication therefore the hub has become obsolete. Replaced by switches and Routers





### Data flow

- Simplex 
- Half Duplex 
- Full Duplex

| SImplex                                                     | Half Duplex                                                | Full Duplex                                      |
| ----------------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------ |
| Communication is unidirectional                             | Communication is bi directional but not a the same time    | Communication is bi directional at the same time |
| Only one device can transmit and the other can only recieve | Both devices can receive and transmit                      | Both devices can receive and transmit            |
| Most cost effective                                         | More cost effective than full duplex but less than simplex | Least cost effective                             |
| Least cost effective to implement                           | More complex to implement than simplex but less than FD    | Most complex to implement                        |
| No way to verify the correctness of data transmitted        | Less reliable than FD but more reliable than simplex       | Most reliable                                    |
|                                                             | Delay is present                                           |                                                  |
| Ex: keyboard to cpu                                         | Ex: Walkie Talkie                                          | Ex: Voice Call                                   |
channel capacity = bandwidth x propogational delay
# References
---

Reference text book is there in [[Networking Index]]

For shorter notes reference [Javtpoint website](https://www.javatpoint.com/computer-network-components)
