Switches operate at Layer 2 and is responsible for communication within **LANs**.

The Data-Link layer provides **node-to-node** connectivity and data transfer. It defines how data is formatted for transmission over a physical medium and detects and possibly corrects Physical layer errors.

# Local Area Networks (LAN)

Routers divide network into LANs. For example, there are four LANs:

![[LANs.png]]

#LAN

# Ethernet Frames

In this layer, the data are encapsulated and transmitted in **Frames**. Review the PDUs in Layer 2. Packets are encapsulated with **Ethernet Header** and **Trailer**. Let's introduce more details about them.

![[Eth. Header and Trailer.png]]

|1 [Preamble](https://dictionary.cambridge.org/zhs/%E8%AF%8D%E5%85%B8/%E8%8B%B1%E8%AF%AD-%E6%B1%89%E8%AF%AD-%E7%AE%80%E4%BD%93/preamble)|2 Start Frame Delimiter (SFD)|3 Destination|4 Source|5 Type| FCS |Total|
|---|---|---|---|---|---|---|
|7 bytes|1 bytes|6 bytes|6 bytes|2 bytes|4 bytes|24 bytes|

## Ethernet Header

### Preamble and SFD

|Field|Preamble|SFD|
|---|---|---|
|Length|7 bytes|1 bytes|
|Alternating|‘101010**10**’*7|‘101010**11**’|
|Function|Allowing devices to synchronize their receiver clocks|Indicating the end of preamble, and the beginning of the rest of the frame|

### Destination and Source

The addresses used in Ethernet are the **destination and source MAC addresses**. MAC means Media Access Control.

|Destination|Source|
|---|----|
|6 bytes| 6 bytes|

### Type or Length

|Type or Length|
|---|
|2 bytes|

#### Length of Packet

**A value of 1500 or less** in this field indicates the Length of the encapsulated packet (in bytes).

#### Type of the encapsulation

**A value of 1536 or greater** in this field indicates the Type of the encapsulated packet and the length is determined via other methods. Usually, there are two types:

|Type|
|---|---|
|**0x0800**=IPv4|‘0x’ indicate [hexadecimal](https://dictionary.cambridge.org/zhs/%E8%AF%8D%E5%85%B8/%E8%8B%B1%E8%AF%AD-%E6%B1%89%E8%AF%AD-%E7%AE%80%E4%BD%93/hexadecimal?q=hexadecimal+), ‘0800’ in hexadecimal is equal to ‘2048’ in [decimal](https://dictionary.cambridge.org/zhs/%E8%AF%8D%E5%85%B8/%E8%8B%B1%E8%AF%AD-%E6%B1%89%E8%AF%AD-%E7%AE%80%E4%BD%93/decimal?q=decimal+)|
|**0x86DD**=IPv6|‘86DD’ in hexadecimal is equal to ‘34525’ in decimal|
|**0x0806**=ARP|

![[ARP Type.png]]

## Ethernet Trailer

The Ethernet trailer has only one field

|Frame Check Sequence (FCS)|
|---|
|Used by the receiving device to detect any errors that might have occurred in transmission.|
|4 bytes|

It detects [corrupted](https://dictionary.cambridge.org/zhs/%E8%AF%8D%E5%85%B8/%E8%8B%B1%E8%AF%AD-%E6%B1%89%E8%AF%AD-%E7%AE%80%E4%BD%93/corrupt?q=corrupted+) data by running a **Cyclic Redundancy Check (CRC)** algorithm over the received data.

## Ethernet Frame Minimum size

The minimum size for an Ethernet frame (Header+Payload/Packet+Trailer) is **64 bytes**. This is a very important size. We'll see it later.

Therefore the minimum payload size is 46 bytes (64 bytes-18 bytes).

If the payload is less than 46 bytes, [padding](https://dictionary.cambridge.org/dictionary/english-chinese-traditional/padding?q=padding+) bytes are added, and these bytes are all 0s.

For example, if we If we send 36-byte [[Layer 3 Ping|pings]], there should be 10 bytes of padding, because the minimum payload size for an Ethernet frame is 46 bytes. 

![[Padding.png]]

These "0" are hexadecimal zeros. Each hexadecimal digit is 4 bits. 10 bytes of padding means there should be 20 zeros.



# MAC address

A **MAC address** is a 6-byte, 12 hexadecimal numbers, physical address assigned to the device when it is made, also known as **Burned-In address**. 

This is different from an **IP address**, which you assign in the CLI when you configure the device.

The MAC address is globally unique, no two devices in the world should have the same MAC address. Although, there are MAC address known as ‘locally-unique’ MAC address, which don’t have to be globally unique throughout the world.

| First 3 bytes|Second 3 bytes|
|---|---|
|the **OUI (Organizationally Unique Identifier)**, which is assigned to the company making the device. |Unique to the device itself.|
|AAAAAA|000001|

# MAC-based switching
## Unknown Unicast Frame

![[LAN Switching 1.png]]

Look at the interface name F0/1. **F** means Fast Ethernet, so these are 100 Mbps interfaces.

PC 1 sends the frame through its **Network Interface Card (NIC)**, which is connected to SW1 and SW1 receives the frame. 

After SW1 receives the frame, it looks at the source MAC address field of the frame, and uses that information to learn where PC1 is. **It insert the MAC address to it’s MAC address table, and it associates that MAC address with it’s F0/1 interface.**

This is known as dynamically learned MAC address or **Dynamic MAC Address**.

![[LAN Switching 2.png]]

Every switch will keep a MAC address table like this, and they fill the MAC address table dynamically by look at the source MAC address of frames it receives. 

But SW1 doesn’t know where the destination is. This frame is called **Unknown Unicast Frame**, a frame for which the switch doesn’t have an entry in its MAC address table.

![[LAN Switching 3.png]]

For unknown unicast frame, switch has only one option, that is to flood the frame. **Flood means to forward the frame out of all of its interfaces, except the one it receives the packet on.** So, SW1 copies the frame and sends it out its F0/2 and F0/3 interfaces.

PC3 ignores the packet, because the destination MAC address doesn’t match its own MAC address, it simply drops the packet. PC2 receives the packet and then processes it normally, up the OSI stack (de-encapsulation).

## Known Unicast Frame

![[LAN Switching 4.png]]

Now, let’s say PC2 wants to send some data to PC1, maybe a reply to what PC1 sent to PC2. The destination and source addresses of the frame are reversed. PC2 sends the frame out of its network interface and SW1 receives it.

**SW1 looks at the source MAC address of the frame, and then adds it to its MAC address table, associating it with the F0/2 interface**. 

This frame is called as a **Known Unicast frame**, because the destination is already in its MAC address table.

**Known unicast frames are simply forwarded to the destination**.

Then, PC1 the processes the frame up the OSI stack, through the de-encapsulation process.

On Cisco switches, these MAC addresses are removed from the MAC address table after **5 minutes of inactivity by default**.

What's more, switch learns MAC address and the MAC address table indicates the interface it can use to reach PC1. **It doesn’t mean that the PC1 directly connects to F0/1 interface.** The switch might transmit the frame to another switch.

![[LAN Switching 5.png]]

Just so we’re clear, the **switch uses the Source MAC Address field to fill its MAC address table**, because if it receives a frame from that source on the interface, it knows that it can reach than MAC address via that interface.

# Address Resolution Protocol (ARP)

Now, let's go back the the previous step. 

When a device sends some data to another device, it doesn’t just include a source and destination MAC address. Encapsulated within that frame is an IP packet, and that IP packet includes a **Source and Destination IP address**.

![[ARP 1.png]]

However, when PC1 prepares to send data to PC3 for the first time, it doesn't know the MAC address of PC3. PC1 has to discover PC3’s MAC address by itself.

To do so, it uses something called ARP, the **Address Resolution Protocol**. ARP is used to discover the Layer 2 address of a known Layer 3 address

The ARP process consists of two messages:

|ARP Request|ARP Reply|
|---|---|
|Sent by the device that wants to know the MAC Address of other device|Sent to inform the requesting device of the MAC address|
|Broadcast =Sent to all hosts within the LAN| Uicast=Sent only to the host that sent the request|

## ARP Request

Before sending the original frame, PC1 has to send ARP Request frame.

![[ARP 2.png]]

In ARP Request frame, **Dst MAC address ‘FFFF.FFFF.FFFF’ is the broadcast MAC address**. 

When SW1 receives ARP Request frame from G0/0, it will broadcast the frame out of all of its interfaces, except the one it was received on. PC2 drops the frame. SW2 floods the frame to PC3 and PC4.

## ARP Reply
After receiving the ARP Request frame, PC3 send the ARP Reply frame. It can send the ARP reply directly to PC1, without having to broadcast the frame.

![[ARP 3.png]]

PC1 will then use that information to add an entry for PC3 to its **ARP Table**, which is used to store these IP address to MAC address associations.

## ARP table

Use command "arp -a" in CMD to view the ARP table (Windows, macOS, Linux).

![[ARP 4.png]]

In Cisco IOS, use this command to view the ARP table.

```
SW#show arp
```

Here‘s the ARP table.

![[ARP 5.png]]

#ARP 

Hopefully you understand this process a little better now:

If device A wants to send traffic to device B, which is on the same network, device A has to use ARP to learn device B's MAC address, and then it can send traffic to device B.

# MAC address table on a Cisco switch

To view the MAC address table on a Cisco switch, we use these command.

```
SW#show mac address-table   #for newer versions
SW#show-mac-address-table   #for old versions

```

![[MAC Table 1.png]]

**Vlan** means **Virtual local area network**, **the default is 1**. We'll learn it later.

Do you remember that? MAC addresses are removed from the MAC address table after 5 minutes of inactivity by default. This is known as **Aging**.

We can manually remove all dynamic MAC addresses from the table using:

```
SW#clear mac address-table dynamic

```

![[MAC Table 2.png]]

If you don't want to clear all of the MAC addresses from the table, you can add some additional option to the command.

```
SW#clear mac address-table dynamic addres 02fc.2ab1.fda2
SW#clear mac address-table dynamic interface g0/0

```

# References

>[Jeremy's IT Lab CCNA Day 5](https://www.youtube.com/watch?v=SDocmq1c05s&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=9)
>
>[Jeremy's IT Lab CCNA Day 6](https://www.youtube.com/watch?v=5q1pqdmdPjo&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=11)


# Late collision

![[Late collision.png]]