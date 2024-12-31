
2024-06-07 19:25


Status: #NetworkingBasics #OSI

Tags: [[Networking Index]]

# OSI Model

OSI (Open System Interface) was developed by ISO (International Standard Organisation) its a conceptual framework which is used to simplify communication especially network communication  
  
The OSI Model has 7 layers
![[OSI Model.png]]
The Top 3 layers are called the **host layers**  
  
**7** **:** **APPLICATION** Handles services and programs that use network to transmit and receive data -→ websites, email clients, etc (HTTP, SMPT)  

**Protocols Used:**
- HTTPS (Hyper Text Transfer Protocol)
- SSH (Secure Shell)
- SMTP (Simple Mail Transfer Protocol)
- FTP (File Transfer Protocol)
  
**6** **:** **PRESENTATION** Handles compression/decompression , encoding/decoding basically making it usable for the adjacent layers (5 for receiving data and 7 for sending it) (JPEG, JPG)  

**Protocols Used:**
- Same as Application Layer
  
**5 :** **SESSION** This layer is responsible for setting up, maintaining, and tearing down sessions, in addition to performing functions like authentication and authorisation (Session management)   

**Protocols Used:**
- Same as Application Layer
  
The Bottom 4 layers are called the **media layers**  
  
**4:** **TRANSPORT** This is the layer that handles ports. You know, like HTTP at port 80, HTTPS at port 443. Being responsible for data delivery, this layer also handles breaking large data transfers into pieces for delivery, and then reconstituting them at the other end.  
  
There are two main protocols that are used at this layer: **TCP** and **UDP**.  
  
**TCP** sends segments of data, and has delivery guaranteeing mechanisms in it, such as checking packets for errors, ensuring they are received in the correct order, and re-transmitting when packets are dropped. This ensures high fidelity communication, but these checks and balances come at a cost of speed. If you want speed – the name of the game when streaming media such as video games or movies – you use UDP.  
  
**UDP** sends data grams and doesn’t care whether they make it or not – fire them off, and yell “catch!” A few dropped packets is unlikely to ruin your kill streak, so you can do away with that error-checking overhead to satisfy your need for speed.  
  
**3:** **NETWORK**Transmitting data between devices in different networks, i.e., routing! This is the province of IP addresses, the logical addresses assigned to hosts.  
Routers are layer 3 devices that enable communication across networks by routing packets between those devices based on IP addresses. (Routing, IP Addresses)  

**Protocols Used:**
- IP(Internet Protocol)
- ARP(Address Resolution Protocol)
  
**2:** **DATA LINK** Transmitting data between nodes on a network, i.e., switching, This is the province of MAC addresses, the physical addresses assigned to **Network Interface Cards**.Read more here -> [[CN_MOD_1]]  

Switches are Layer 2 devices that enable communication on a local network by forwarding frames between those devices. Ever heard of packets? Frames are like packets, but on Layer 2. (Switching, MAC Addresses)  

**Protocols Used:**
- WiFi
- ARP(Address Resolution Protocol)
  
**1:** **PHYSICAL** Transmitting data over a physical medium, such as a cable or over-the-air.  
The building blocks of communications between electronics – electrical signals and the various low-level data units they represent (bits, or binary digits, and symbols). (Optical cables , cat6)
**Protocols Used:**
- WiFi
- Ethernet

**Transmission Mode:**
- Simplex
- Half Duplex
- Full Duplex

![[OSI Layers.png]]
**L7-L1**  
All People Seem To Need Data Processing  
Application Presentation Session Transport Network Data Link Physical  
  
**L1-L7**  
Please Do Not Throw Sausage Pizza Away  
Physical Data Network Transport Session Presentation Application  
  
  
While OSI is a very effective model it can only be applied in theory due to the limitations of creating and managing these many layers  
  
So a more practical approach was formed which is known as TCP/IP  
  
When trouble shooting go from down to up (physical->application)

# References
---

Forgot the references will pin it up when i pick up this topic later