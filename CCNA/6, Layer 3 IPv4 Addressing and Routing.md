Layer 3 in OSI model, Network Layer provides connectivity between end hosts on different networks (i.e. outside of the LAN).

It also provides **logical addressing (IP addresses)**.

Layer 3 provides path selection between source and destination.

Router operate at Layer 3.

# Internet Protocol (IP)

Internet protocol is the primary Layer 3 protocol in use today. Version 4 is the version in use in most networks.

Review the PDU of Layer 3, segments are encapsulated with **Layer 3 Header** to form packets.

## IPv4  Header

![[IPv4 Header.png]]

Now, let's look at the **Source IP address** and the **Destination IP address**.

These fields, as well as IP addresses, are 32-bits or 4 bytes in length.

## IPv4 Addresses

![[IPv4 address.png]]

Common IPv4 addresses are written in human readable format, **dot decimal**.

**Every group of numbers represent 8 bits.**

The range of possible numbers that can be represented with 8 binary bits ranges from 0 (00000000) to 255 (11111111).

You'll often hear each of these 8 bit groups referred to as **Octet**. 

You should watch the video in the end to master decimal-to-binary or binary-to-decimal conversion.

## IPv4 Address Classes

Now, IPv4 addresses are split up into 5 different ‘classes’. The class of an IPv4 address is determined by the first octet of the address.

| | Class| First octet | First octet numerical range| Prefix Length |
|---|---|---|---|---|
||A|0xxxxxxx|0-126 (127)| /8|
||B|10xxxxxx|128-191| /16|
||C|110xxxxx|192-223| /24|
|multicast addresses|D|1110xxxx|224-239| |
|reserved (experimental)|E|1111xxxx|240-255| |

### Loopback Addresses 127.0.0.0/8

Address range 127.0.0.0-127.255.255.255 are used to test the **network stack** on the local device.

If we ping an IP address in this range, the PC is just sending and receiving these pings to and from itself.

![[Loopback Address.png]]

### IPv4 Network Address

**The first address in each network is the network address, it cannot be assigned to hosts.**

### IPv4 Broadcast Address

**The last address of the network is the broadcast address, the Layer 3 address used when you want to send traffic to all hosts on the local network, it also cannot be assigned to hosts.**

### Netmask

When we configure or allocate IPv4 address, it is impossible to enter hundreds and thousands addresses one by one. So, we represent an entire IP address block by appending the **prefix length** to the address.

There are two format to express a prefix length. One is like "/8", "/24", etc.

Cisco devices still use an older, slightly more complicated way of writing the prefix length: **a dotted decimal netmask**.

![[Netmask.png]]

In binary, "1" indicates the **Network portion**, and "0" indicates the **Host portion**.

Network portion is the code to identify a network. For example, 192.168.0.0/24 and 192.168.1.0/24 indicate two different networks. So, we could create 128 networks in Class A, from 0.0.0.0/8 to 127.0.0.0/8. 

Host portion is the code to identify a host. For example, 192.168.1.1 and 192.168.1.2 indicate two different hosts in one network.

Think of "1" as "Block/Lock" and "0“ as "Open/Free".

Therefore, "192.168.0.0/24" or "192.168.0.0  255.255.255.0" indicates a block of 256 addresses from 192.168.0.0 to 192.168.0.255.

Did you remember the Network and Broadcast address? In the 192.168.0.0/24 block, 192.168.0.0 is the Network address, and 192.168.0.255 is the Broadcast address. They cannot be assigned to hosts. 

From 192.168.0.1 to 192.168.0.254, these 254 addresses are host addresses. Each address represents a network user in the 192.168.0.0/24 block, if you allocated an address to them.

Of course, network 192.168.0.0/24 belongs to Class C.

### Maximum Hosts per Network

My smart reader, you must have figured out the answer of how to calculate maximum hosts for an IPv4 address block. It equals to **Addresses per network - 2**. 

Try to calculate the maximum hosts per network for each network class now! The answer is here, and are you right?

| Class | Maximum Hosts per Network|
| --- | --- |
| A | 256 × 256 × 256 -2|
| B | 256 × 256 - 2|
| C | 256 -2 |

> [Jeremy's IT Lab CCNA Day 7 & 8](https://www.youtube.com/watch?v=3ROdsfEUuhs&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=13)
> [[6.2 Router Configuration-Interface]]
