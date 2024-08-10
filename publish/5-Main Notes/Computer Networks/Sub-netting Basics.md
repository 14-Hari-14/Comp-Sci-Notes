
2024-06-07 19:27


Status: #NetworkingBasics  #Sub-netting

Tags:[[Networking Index]]

# Sub-netting Basics

Sub-net masks take a part of ur IP address and splits it into groups this helps a consolidate a lot of IP addresses on one network to the same group  
there are 3 classes to sub-net masks  
  
**Class A: 255.0.0.0**  
This is the largest group available it can hold 256^3 = 16,777,216 - 2 devices at once since the zeroes in the address can range from 0 to 256  
Its used by large corporations with many employees. The first bit is used to identify the network while the other three are used for host addresses  
  
**Class B: 255.255.0.0**  
This is second largest group available it can hold 256^2 = 65,536 - 2 devices. The first 2 bit are used to identify the network while the other 2 are used for host addresses  
  
**Class C: 255.255.255.0**  
This is the most common group since its used by households and small businesses it can hold 256 - 2 devices at once which is more than necessary for most households and small businesses.  
The first 3 bits are used to identify the network while the last bit is used to hold host addresses  
  
**the -2 is done to calculate the actual number of addresses for devices since 1 addresses is taken for network id and the other one by broadcast id**

	![[subnettingtable.png]]

**Advantages of sub-netting**  
  
  
1. **Conservation of IP Addresses:** Sub-netting allows for more efficient use of IP addresses by breaking down a larger network into smaller sub-nets. This is particularly important due to the limited availability of IPv4 addresses. This is the reason why we can still use IPv4 even when the number of devices have exceeded the number of IP addresses in IPv4  
  
2. **Network Segmentation:** Sub-netting helps in dividing a large network into smaller segments, which can improve network performance, security, and management. By logically separating different departments, floors, or buildings within an organisation into separate sub-nets, network traffic can be contained and managed more effectively.  
  
3. **Reduced Broadcast Traffic**: In large networks, broadcast traffic can become a significant burden, consuming network bandwidth and resources. Sub-netting reduces the size of broadcast domains by creating smaller, more localised sub-nets, which helps in minimising broadcast traffic.  
  
4. **Improved Security**: Sub-netting allows for better network security by logically isolating different parts of the network from each other. By segmenting the network into smaller sub-nets, it becomes easier to implement and manage access control policies, firewalls, and other security measures to protect sensitive data and resources.  
  
5. **Scalability**: Sub-netting facilitates network growth and scalability by providing a flexible framework for expanding and adding new sub-nets as needed. It allows organisations to easily accommodate new devices, users, and services without requiring a complete redesign of the network architecture.  
  
6. **Routing Efficiency**: Sub-netting enhances routing efficiency by breaking down a large routing table into smaller, more manageable segments. This reduces the overhead associated with routing updates and improves overall network performance.


# References
----

Forgot the references will pin it up when i pick up this topic later