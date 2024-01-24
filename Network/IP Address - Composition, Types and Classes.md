# IP Addresses – Composition, Types and Classes

Before heading deeper into IP addresses, you should be aware of the following terms

- **Bit –** A bit is a single digit with a value of 0 or 1.
- **Byte –** A byte is composed of 8 bits.
- **Octet –** An octet is also made up of 8 bits. Throughout this chapter the terms byte and octet are interchangeable.
- **Network Address –** This refers to a remote network in terms of routing. All hosts in the remote network fall within this address. For example, 10.0.0.0, 172.16.0.0 and 192.168.1.0
- **Broadcast Address –** This is the address used to send data to all hosts in a network. The broadcast address 255.255.255.255 refers to all hosts in all networks while an address such as 192.168.1.255 refers to all hosts in a particular network.

An IP address is 32 bits in length. To make the address easier to read, it is divided into four sections of 8 bits each divided by a period. Each section is therefore, 1 byte (also called octet) long. To further make it easier to read and remember, the binary numbers are converted to decimal. For example, an IP address such as 11000000100000000000110000000001 is divided to make it 11000000.10000000.00001100.00000001. When this address is converted to decimal, it will become 192.128.12.1. This format of IP address is called the **dotted decimal** format. Some applications also covert the address to hexadecimal format instead of decimal format. However this is not commonly seen and as far as the CCNA exam is concerned, you need to only work with the dotted decimal format.

Topics in this chapter require binary to decimal conversions. Table 2-1 shows the decimal value of each bit location in a byte. To easily convert from binary to decimal, add up the decimal value corresponding to the bit place that is “on” (1). For example, a binary value of 10110000 can be easily converted to decimal by adding the decimal value of each bit that is 1. That gives us 128+32+16 = 176.

Table 2-2 shows the decimal value for the most common binary numbers you will encounter in this chapter.

**Table 2-1** _Decimal Value for each bit place in a byte_

|   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|
|128|64|32|16|8|4|2|1|

**Table 2-2** _Decimal Values for common binary numbers_ 

|   |   |
|---|---|
|**_Binary Value_**|**_Decimal Value_**|
|**_10000000_**|_128_|
|**_11000000_**|_192_|
|**_11100000_**|_224_|
|**_11110000_**|_240_|
|**_11111000_**|_248_|
|**_11111100_**|_252_|
|**_11111110_**|_254_|
|**_11111111_**|_255_|

An IP address does not only represent the host address. In fact it represents the network where the host resides and the host it self. In effect, the IP address consists of two parts:

1. **1.**    **The Network component** – Defines network (or **subnet)**, in an internetwork, the host resides in.
2. **2.**    **The Host component** – Defines the host itself in the network.

Each combination of the network component and the host component should be unique in the entire Internetwork. To make it easy to identify which portion of the address is network component and which one is the host component, addresses are broken down into 5 classes discussed below:

- **Class A** – The first byte (8 bits) is the network component and the remaining three bytes (24 bits) are host component (network.host.host.host). This class is for an internetwork with small number of networks and large number of hosts per network.

- **Class B** – The first two bytes (16 bits) are the network component and the remaining three bytes are host components (network.network.host.host). This class bridges the gap between Class A and Class C by providing for medium number of networks with medium number of hosts.

- **Class C** – The first three bytes (24 bits) are the network component and the last byte (8 bits) is the host components (network.network.network.host). This class provides for large number of networks with fewer hosts per network.

- **Class D** – Used for multicasting.

- **Class E** – Reserved addresses

In a binary address the first 5 bits of the address and the first octet in a dotted decimal address shows the class of address. Table 2-3 shows the first 5 bits and the first octet range of each class of address.