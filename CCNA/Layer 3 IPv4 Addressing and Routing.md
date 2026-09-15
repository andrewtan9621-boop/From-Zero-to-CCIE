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

### Network Address

**The first address in each network is the network address, it cannot be assigned to hosts.**

### Broadcast Address

**The last address of the network is the broadcast address, the Layer 3 address used when you want to send traffic to all hosts on the local network, it also cannot be assigned to hosts.**

### Netmask




# Routing 

![[Routing 1.png]]

Router splits the network into 2 LANs.

If PC1 sends a frame to the broadcast MAC address, SW1 will receive the frame and forward it out of all of interfaces except the frame was received on. PC2 and R1 receive the frame.

![[Routing 2.png]]

However, that’s where it ends. **The broadcast is limited to the local network, it doesn’t cross the router.**

