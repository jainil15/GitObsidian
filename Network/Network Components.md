# 1-1 Introduction to Networks

9–11 minutes

---

Before you learn Cisco Internet working, it is important to understand what a network is and the importance of networks themselves. Simply put, a network is a collection of interconnected devices (such as computers, printers, etc.). To understand the importance of networks, let us look at how things worked before networks were created. For this, consider a large multinational company that sells food products in a time when networks did not exist.

Let us call this company ABC Inc. Imagine the amount of information such as sales, inventory, etc. required by the management of the company to make everyday decisions. To get this information they will need to call their local offices. Their local offices will need to mail (postal!) or fax printed reports or even send media though the postal service. By the time the mail is received, the data is already days old. Even if reports are faxed, it will be a cumbersome task to consolidate all reports. This task also increases chance of human error since large numbers of reports are manually collated. This is just one part of the equation. You also need to consider the information required by the local offices. They also need various data from the head office and other offices around the world.

Now consider the same company, but in the present time with all their offices interconnected. They would use a single application around the world that takes advantage of their global network. The data from all offices would be instantly stored at the central location and with a single click, the management team can see data from around the world in any format they like. This data would also be real-time. This means that they see it as its happening. Since the data is centralized, any office location can see data pertaining to any location.

As you can see, the cost, time and effort involved in transferring data was much higher without networks. So networks decrease cost, time, and effort and thereby increase productivity. They also help in resource optimization by helping to share resources. A simple example of resource sharing is a printer in a typical office. Without networks, each computer would require a dedicated printer. However with a network, the printer can be shared between many different computers.

Now that you know how beneficial networks are, its time to look at how networks work. Figure 1-1 shows the most basic form of a network. This figure shows two hosts (end-user devices such as computers are commonly called hosts in networking terms) directly connected to each other using a networking cable. Today every host has a **Network Interface Card (NIC)** that is used to connect it to a network.

**Figure 1-1** _Most basic form of Network_

 _![1](https://s8185.pcdn.co/wp-content/uploads/2013/10/11.png)_

One end of the network cable connects to the NIC on a host and the other connects to the network. In this case, the cable directly connects to another host. At this stage do not worry about network cables and how the hosts communicate across the network. This will be covered in detail later in the chapter. At this stage it is important to understand how hosts connect to a network.

In Figure 1-1, the hosts are “networked” and can share information. This network is effective, but not scalable. If you have more than 2 hosts to this “network”, it will not work without a separate NIC card for each connection and that is not scalable or realistic. For more than 2 hosts to be networked, you require a network device such as a **hub**. Figure 1-2 shows three hosts connected to a hub.

**Figure 1-2** _Network with a Hub_

![2](https://s8185.pcdn.co/wp-content/uploads/2013/10/2.png)

A hub is a network device that repeats information received from a host to all other connects hosts. In Figure 1-2 the hub will relay any information received from HostA to HostB and HostC. This means that all the three hosts can communicate with each other. Communication between hosts can be classified into three types:

- **Unicast** – Communication from one host to another host only.
- **Broadcast** – Communication from one host to all the hosts in the network.
- **Multicast** – Communication from one host to few hosts only.

When a hub is used to network hosts, there are two problems that arise:

1. A hub repeats information received from one host to all the other hosts. To understand this, consider HostA in Figure 1-2 sending a unicast message to HostB. When the hub receives this message; it will relay the message to both HostB and HostC. Even though the message was a unicast intended only for HostB, HostC also receives it. It is up to HostC to read the message and discard it after seeing that the message was not intended for it.
2. A hub creates a shared network medium where only a single host can send packets at a time. If another host attempts to send packets at the same time, a collision will occur. Then each device will need to resend their packets and hope not to have a collision again. This shared network medium is called a single **collision domain.** Imagine the impact of having a single collision domain where 50 or 100 hosts are connected to hubs that are interconnected and they are all trying to send data. That is just a recipe for many collisions and an inefficient network.

The problems associated with hubs can cause severe degradation of a network. To overcome these, **switches** are used instead of hubs. Like hubs, switches are used to connect hosts in a network but switches break up collision domain by providing a single collision domain for every port. This means that every host (one host connects to one port on the switch) gets its own collision domain thereby eliminating the collisions in the network. With switches, each host can transmit data anytime. Switches simply “switch” the data from one port to another in the switched network. Also, unlike hubs, switches do not flood every packet out all ports. They switch a unicast packet to the port where the destination host resides. They only flood out a broadcast packet. Figure 1-3 shows a switched network.

**Figure 1-3** _A switched network_

  _![3](https://s8185.pcdn.co/wp-content/uploads/2013/10/3.png)_

Remember that each host in Figure 1-3 is in its own collision domain and if HostA sends a packet to HostC, HostB will not receive it.

Figure 1-4 and 1-5 show two networks. See if you can figure out how many collision domains exist in them.

**Figure 1-4** _Collision Domains – 1_

 _![4](https://s8185.pcdn.co/wp-content/uploads/2013/10/4.png)_

**Figure 1-5** _Collision Domains – 2_

  _![5](https://s8185.pcdn.co/wp-content/uploads/2013/10/5.png)_

If you answered 5 for Figure 1-4, then you are absolutely correct since each port of the Switches represent a single collision domain. If you answered more than 5 then you need to remember that a hub does not break collision domains. Similarly, Figure 1-5 has 7 collision domains.

Now that you know how a switch works and improves a network, consider the one problem associated with a switched network. Earlier, you learned that hubs flood out all packets, even the unicast ones. A switch does not flood out unicast packets but it does flood out a broadcast packet. All hosts connected to a switched network are said to be in the same **broadcast domain**. All hosts connected to it will receive any broadcast sent out in this domain. While broadcasts are useful and essential for network operations, in a large switched network too many broadcasts will slow down the network. To remedy this situation, networks are broken into smaller sizes and these separate networks are interconnected using **routers**. Routers do not allow broadcasts to be transmitted across different networks it interconnects and hence effectively breaks up a broadcast domain. Figure 1-6 shows three switched networks interconnected by a router. 

**Figure 1-6** _Router in an Internetwork_

 _![6](https://s8185.pcdn.co/wp-content/uploads/2013/10/6.png)_

In the network shown in Figure 1-6, broadcasts from hosts connected to Switch1 will not reach hosts connected to Switch2 or Switch3. This is because the router will drop the broadcast on its receiving interface.

In addition to breaking up broadcast domains, routers also perform the following four essential functions in your network:

- **Packet Switching** – At the barest minimum, routers are like switches because they essentially switch packets between networks.
- Communication between Networks – As shown in Figure 1-6, routers allow communication between networks connected to it.
- **Path Selection** – Routers can talk to each other to learn about all the networks connected to various routers and then select the best path to reach a network. This is function is discussed in detail later in the book.
- **Packet Filtering** – Routers can drop or forward packets based on certain criteria like their source and destination. This is also discussed in detail later in the book.

![img](https://s8185.pcdn.co/wp-content/plugins/wp-special-textboxes/images/info.png)

**Exam Alert**: Remember that switches break collision domains and routers break broadcast domains. In addition to that it is important to remember the functions of a router for your CCNA certification exam.

Now that you know what a network is and what various network devices do, its time to learn about various network types followed by networking models.