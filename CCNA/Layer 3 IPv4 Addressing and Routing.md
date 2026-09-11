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

## IPv4 addresses

![[IPv4 address.png]]

Common IPv4 addresses are written in human readable format, **dot decimal**.

**Every group of numbers represent 8 bits.**

The range of possible numbers that can be represented with 8 binary bits ranges from 0 (00000000) to 255 (11111111).

You'll often hear each of these 8 bit groups referred to as **Octet**. 

You should watch the video in the end to master decimal-to-binary or binary-to-decimal conversion.






# Routing 

![[Routing 1.png]]

Router splits the network into 2 LANs.

If PC1 sends a frame to the broadcast MAC address, SW1 will receive the frame and forward it out of all of interfaces except the frame was received on. PC2 and R1 receive the frame.

![[Routing 2.png]]

However, that’s where it ends. **The broadcast is limited to the local network, it doesn’t cross the router.**

