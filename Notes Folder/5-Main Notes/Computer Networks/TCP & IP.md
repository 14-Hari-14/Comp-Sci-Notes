	
2024-06-07 19:28


Status: #NetworkingBasics  #TCP/IP

Tags:[[Networking Index]]

# TCP & IP

  
TCP/IP (Transfer Control Protocol/ Internet Protocol)  
  
1. Layer 1: Network Access  
2. Layer 2: Internet
3. Layer 3: Transport  
4. Layer 4: Application

![[OSIvsTCP.png]]

Pnemonic(level 1 to level 4)
<font size =10><b>A TIN</b></font size>    
  
In practice, the TCP/IP model provides the following:  
1. Forms the basis of the Internet and other large-scale networks  
2. Provides a simplified, more practical approach to network communications, relative to the OSI model  
3. Serves as the universal standard for network communication, given its wide adoption and implementation by a wide variety of devices and applications.


![[tcpencap&decap.png]]

  
TCP works on a 3 way handshake  
  
<font size =10><b>SYN > SYN ACK > ACK  </b></font size>
  
so how a three way handshake works is I want to visit a website so I send a SYN packet to a specific port of that website(the port is decided by which protocol is being used right now)  

if that port is free I get a SYN ACK packet back saying that the port is available for connection  

now if the final connection is established I send an ACK packet saying that the connection has been established  
  
Common Ports and Protocols  
TCP  

**FTP(21)** file transfer protocol  
**SSH(22)** secure socket shell or secure shell (encrypted telnet) |- remote login to computer  
Telnet(23)  
  
DNS(53) |- resolve IP addresses to names (domain name system)  
HTTP(80)/HTTPS(443) hyper text transfer protocol (secure)  
  
SMB(139+45) |- files shares  
  
POP3(110) |  
SMTP(25) |- related to mails  
IMAP(143) |  
  
UDP  
DNS(53)  
DHCP(67, 68) |- gives a random IP address to use internet  
TFTP(69) trivial ftp  
SNMP(161) simple network management protocol


# References
----

Forgot the references will pin it up when i pick up this topic later