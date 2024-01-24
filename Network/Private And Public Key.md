**Public IP Address:** A public IP address is a globally unique address that is assigned to a device or network and is used for communication over the internet. Public IP addresses are routable on the public internet, allowing devices with public IPs to communicate directly with other devices or services on the internet.

Subnetting allows you to borrow some host bits and use them to create more networks. These networks are commonly called **subnets** and are smaller in size. But since each network has a network address and a broadcast address, some addresses get wasted

VLSM is subnetting as subnet.

1. The TCP segment is handed off to IP, which adds a header consisting of the source address, 192.168.1.10 and destination address 192.168.5.20 and hands off that packet to the next layer.
2. Using the subnet mask of the host, it is determined that the destination address lies in a remote network and hence the packet must be sent to the default gateway, 192.168.1.1. So Host1 sends out an ARP request to find the MAC address of Router1. When a response is received, it frames the packet with the source MAC address of Host1 and destination MAC address of Router1.
3. When Router1 receives the frame, it strips of the header and trailer and looks at the destination address in the IP header. Since the packet is not destined to Router1, it must be routed out.
4. It tries to match the destination address to a list of known networks, called the routing table. It finds that the destination network is reachable via Router2, so it frames the packet with the source MAC address of its exit interface (interface with the IP address of 10.1.1.1) and the destination address of Router2’s interface.
5. When Router2 receives the frame, it repeats the strip and lookup process and frames the packet again before sending it to Router3. This time the MAC address of Router2’s exit interface is the source address while the MAC address of Router3 is the destination address.
6. Finally Router3 looks at the destination MAC address and realizes that the destination network is directly connected. It finds the MAC address of the destination host and frames the packet using its own MAC address as the source while the MAC address of Host3 as the destination address. At last the frame is sent out and reaches the destination host.
7. At the destination, the frame is stripped and the destination IP address is verified. Then the IP header is stripped and the TCP segment reaches Layer 4 of the destination.
8. Now when Host3 needs to reply back to Host1, TCP will hand off the reply segment to IP.
9. IP will add a header consisting of a source address of 192.168.5.20 and a destination address of 192.168.1.10 and will send it to layer 2 for framing.
10. By the subnet mask of Host3, it is determined that the destination lies in a remote network. Hence the frame will need the MAC address of the default gateway as destination. If Host3 does not have the MAC address of Router3, it will send an ARP query to get it. Once Host3 has the MAC address, it will frame the segment and send it out to Router3.
11. Router3 strip the frame header and look at the destination IP address in the IP header. From its routing table, it will know that the packet needs to go to Router2. It will frame the packet with a source MAC address of its fa0/0 interface and the destination MAC address will be the address of Router2’s fa0/1 interface and then send it out to the wire.
12. Router2 receives the frame and repeats process to send the packet to Router 1.
13. Router1 receives the frame from Router2 and removes the frame. By the destination IP address it knows that the packet belongs to a directly connected interface.
14. Since it received a frame from Host1 earlier, it has the MAC address of the host mapped to its IP address in the ARP table. The router uses that to create a frame with its fa0/0 interface’s MAC address as source and Host1’s MAC address as destination and sends the frame out the interface.
15. When Host1 receives the frame, it verifies the destination address, strips the frame and IP header and sends the TCP segment to layer 4.

### Static 
![img](https://www.freeccnastudyguide.com/study-guides/ccna/ch4/routing/)

**ip route** _destination_network mask {next_hop_address | exit_interface}_

e.g, 
Router1(config)#ip route 192.168.5.0 255.255.255.0 10.1.1.2
Router2(config)#ip route 192.168.5.0 255.255.255.0 10.1.2.2

1. **Static Routing:**
    
    - Static routing involves manually configuring a router or network device to define the paths that network traffic should take. These routes remain fixed unless manually changed by a network administrator. Static routing is straightforward and suitable for small networks with simple, unchanging topologies.
2. **Dynamic Routing:**
    
    - Dynamic routing relies on routing protocols to automatically update and adapt routing tables based on network conditions and changes. Examples of dynamic routing protocols include Routing Information Protocol (RIP), Open Shortest Path First (OSPF), and Enhanced Interior Gateway Routing Protocol (EIGRP). Dynamic routing is ideal for large and complex networks where routes may change frequently.
3. **Default Routing:**
    
    - Default routing, also known as gateway of last resort, is a special type of routing that directs all traffic not matching specific routes to a predefined next-hop address or interface. It is often used in situations where a router serves as a gateway to the internet or another network.
    - code `ip route 0.0.0.0 0.0.0.0 next-hop`

[
**Router1#sh ip route  
**Codes: C – connected, S – static, R – RIP, M – mobile, B – BGP  
D – EIGRP, EX – EIGRP external, O – OSPF, IA – OSPF inter area  
N1 – OSPF NSSA external type 1, N2 – OSPF NSSA external type 2  
E1 – OSPF external type 1, E2 – OSPF external type 2  
i – IS-IS, su – IS-IS summary, L1 – IS-IS level-1, L2 – IS-IS level-2  
ia – IS-IS inter area, * – candidate default, U – per-user static route  
o – ODR, P – periodic downloaded static route

Gateway of last resort is not set

**S    192.168.5.0/24 [1/0] via 10.1.1.2  
**     10.0.0.0/24 is subnetted, 1 subnets  
C       10.1.1.0 is directly connected, FastEthernet0/1  
C    192.168.1.0/24 is directly connected, FastEthernet0/0

**Router2#sh ip route  
**-output truncated–

**S    192.168.5.0/24 [1/0] via 10.1.2.2  
**     10.0.0.0/24 is subnetted, 2 subnets  
C       10.1.2.0 is directly connected, FastEthernet0/1  
C       10.1.1.0 is directly connected, FastEthernet0/0  
**S    192.168.1.0/24 [1/0] via 10.1.1.1**

**Router3#sh ip route  
**-output truncated–

Gateway of last resort is not set

C    192.168.5.0/24 is directly connected, FastEthernet0/1  
10.0.0.0/24 is subnetted, 1 subnets  
C       10.1.2.0 is directly connected, FastEthernet0/0  
**S    192.168.1.0/24 [1/0] via 10.1.2.1**
]

## NAT 
NAT is a feature that allows the internal network of an organization to _appear_ to be using a different IP address space from the outside than what it is actually using. Thus, NAT allows an organization to use private IP addresses that are not globally routable and yet connect to the Internet by translating those private addresses into globally routable addresses.

### Types

- **Static NAT:**   Static NAT performs static address translation allowing one-to-one mapping between local and global addresses. But you should keep in mind that static NAT requires you to have one registered public IP address for every host on your network. As such static NAT has no benefit in terms of IP address conservation. Nevertheless, static NAT is important for the sake of understanding NAT.
- **Dynamic NAT:**   Dynamic NAT performs dynamic address translation mapping unregistered private IP addresses to registered public IP addresses from a pool of available registered IP addresses. You don’t have to statically configure your router to map an inside to an outside address as you would using static NAT. But yet you do have to have enough registered public IP addresses for everyone who’s going to communicate to the Internet. Even dynamic NAT does not help with the issue of IP address conservation.
- **NAT Overload:** NAT overload performs an overload mapping multiple unregistered private IP addresses to a single registered public IP address. It is a many-to-one mapping between private and public addresses and is accomplished using different port numbers. This method is also known as Port Address Translation (PAT). By using PAT or NAT overload, hundreds or even thousands of users can be connected to the Internet using only one real global IP address. This is the most popular NAT type which basically is a form of dynamic map but with multiple unregistered IP addresses mapped to a single registered IP address. Dynamic NAT is one-to-one while NAT Overload or PAT is many-to-one though both forms do the mapping dynamically. NAT Overload is the type of NAT that has enabled us not to run out of IP addresses on the Internet.
## PAT
1>  
R1>enable  
R1#configure terminal  
Enter configuration commands, one per line.  End with CNTL/Z.  
R1(config)#ip nat pool MyPool 67.210.97.1 67.210.97.1 ?  
netmask        Specify the network mask  
prefix-length  Specify the prefix length

R1(config)#ip nat pool MyPool 67.210.97.1 67.210.97.1 netmask 255.255.255.0  
R1(config)#access-list 1 permit 192.168.1.0 0.0.0.255  
R1(config)#ip nat inside source list 1 pool MyPool overload

R1(config)#interface FastEthernet0/0  
R1(config-if)#ip address 192.168.1.1 255.255.255.0  
R1(config-if)#ip nat inside  
R1(config-if)#interface FastEthernet0/1  
R1(config-if)#ip address 67.210.97.1 255.255.255.0  
R1(config-if)#ip nat outside  
R1(config-if)#end  
R1#

---
---
R1#show ip nat translations

R1

---

how ip nat translations


Total active translations: 3 (0 static, 3 dynamic; 3 extended)  
Outside interfaces:  
Serial1/0  
Inside interfaces:  
FastEthernet0/0  
Hits: 135  Misses: 15  
CEF Translated packets: 150, CEF Punted packets: 0  
Expired translations: 12  
Dynamic mappings:  
— Inside Source  
[Id: 2] access-list 1 pool MyPool refcount 3  
pool MyPool: netmask 255.255.255.0  
start 67.210.91.1 end 67.210.91.1  
type generic, total addresses 1, allocated 1 (100%), misses 0  
Queued Packets: 0

## VLAN
VLAN stands for "Virtual Local Area Network." It is a network technology that allows you to create logically segmented networks within a physical network infrastructure. VLANs are commonly used in networking to improve network efficiency, security, and manageability.

Frametagging is adding VLAN identification header to the frame
Trunk is router attached to the VLAN switch

IEEE 802.1Q

## DNS
The Domain Name System (DNS) is a fundamental component of the internet and networking that serves as a distributed, hierarchical database designed to translate user-friendly domain names into IP addresses and vice versa. It plays a critical role in making the internet accessible by allowing users to navigate the web using human-readable domain names instead of numeric IP addresses

Client -> ISP -> DNS -> Root Server -> Client -> TLD Server -> Client -> Authoritative name server.

## Record Types in DNS
In the Domain Name System (DNS), which is a critical component of the internet and networking, various types of DNS resource records are used to store specific types of information associated with domain names. These resource records provide essential data for DNS queries and responses. Here are some most used and important DNS record types:

1. **A (Address) Record:**
    
    - An A record maps a hostname to an IPv4 address. It is used to translate human-friendly domain names (e.g., [www.example.com (Links to an external site.)](http://www.example.com/)) into IP addresses (e.g., 192.0.2.1).
2. **AAAA (IPv6 Address) Record:**
    
    - The AAAA record is similar to the A record but is used to map a hostname to an IPv6 address. It is essential for supporting the transition from IPv4 to IPv6.
3. **CNAME (Canonical Name) Record:**
    
    - A CNAME record is used to create an alias for an existing A or AAAA record. It allows multiple domain names to resolve to the same IP address, simplifying domain management.
4. **MX (Mail Exchange) Record:**
    
    - MX records specify mail servers responsible for receiving email messages on behalf of a domain. These records point to the hostname of the mail server and include a priority value for mail routing.
5. **TXT (Text) Record:**
    
    - TXT records store arbitrary text information associated with a domain. They are often used for various purposes, including domain verification, Sender Policy Framework (SPF) settings for email authentication, and domain ownership validation.
6. **NS (Name Server) Record:**
    
    - NS records identify authoritative name servers for a domain. These servers are responsible for providing DNS information for the domain.
-
LEVELS
Root Name Servers store ip of tld servers
TLD Name servers store of authoritative servers like .com, .uk

1. **Root Domain:**
    
    - At the top of the DNS hierarchy is the root domain, represented by an empty string (""). It doesn't have a human-readable domain name but is denoted by a dot (.) at the end of domain names. Root servers are responsible for managing the root domain and are operated by different organizations around the world.
2. **Top-Level Domains (TLDs):**
    
    - Beneath the root domain are the top-level domains (TLDs). These are the highest level of domains in the DNS hierarchy and include generic TLDs (gTLDs), such as .com, .org, and .net, and country code TLDs (ccTLDs), like .us, .uk, and .de. The organization responsible for managing a specific TLD is the domain's registry.
3. **Second-Level Domains:**
    
    - Below the TLDs are the second-level domains. These are often used for branding or creating subdomains. For example, in the domain "example.com," "example" is the second-level domain. Users and organizations typically register second-level domains with domain registrars.
4. **Subdomains:**
    
    - Subdomains extend the hierarchy further, allowing for more specific addressing. For example, "www" in "[www.example.com (Links to an external site.)](http://www.example.com/)" is a subdomain. Subdomains are created by domain owners or administrators to organize their web services, resources, or networks.
5. **Hostnames:**
    
    - At the lowest level of the DNS hierarchy are hostnames. A hostname can represent a specific device or service within a subdomain. For example, "webserver" in "webserver.example.com" is a hostname. Hostnames map to IP addresses, allowing for precise addressing.

# IMP
2. Working of VLAN, VLAN makes logical partitioning of physical component, VLAN works as if physically connected network are different network and can't directly broadcast message from one LAN to another LAN, we use trunk router 