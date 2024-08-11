
2024-08-11 21:49


Status: 

Tags:

# Module 1

## Basic Terminology

**Networking:**  Its the process of connecting 2 or more computing devices for exchange of information/resources

**Nodes:** Individual devices

**Bandwidth:** The rate of data transmission between 2 nodes 

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


### HUB
**Definition:** Its a hardware device that divides the network connection among multiple devices.

**Working:** 
One computer will send request to the hub. The hub will then take the request and send it over to the network and each node on the network will check if the request is related to them. If no node is found then the request is dropped. 

**Disadvantages:**
This process uses a lot of bandwidth and limits the communication therefore the hub has become obsolete. Replaced by switches and Routers



# References
---

Reference text book is there in [[Networking Index]]

For shorter notes reference [Javtpoint website](https://www.javatpoint.com/computer-network-components)
