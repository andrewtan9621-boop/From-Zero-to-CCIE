The [[OSI Model and TCP-IP Suite#Layer 2 & 1 Datalink and Physical|Physical Layer 1]] sends and receives **bits** as electrical, optical, or radio signals over the medium.

(I suppose you've already known the fundamental knowledge about some terms like "bits", "duplex", etc. If you don't, google it or watch videos in the end.)


# Ethernet

Ethernet is a collection of network protocols/standards, rather than just a single protocol. Ethernet standards were defined in **IEEE 802.3 standard** in 1983. IEEE means Institute of Electrical and Electronics Engineer.

Here's a table of some IEEE Standards for **Copper Ethernet cables**.

| Speed Level | Common Name|Informal Name| IEEE standard | Maximum Length |  
|---|---|---|---|---|  
| 10 Mbps | Ethernet | **10BASE-T**| 802.3i  | 100m |  
| 100 Mbps | Fast Ethernet| **100BASE-T** | 802.3u | 100m |  
| 1 Gbps | Gigabit Ethernet| **1000BASE-T** | 802.3ab | 100m |  
| 10 Gbps | 10 Gig Ethernet| **10GBASE-T** | 802.3an | 100m |

**BASE** refers to baseband signaling. **T** means twisted pair cabling.

And here's another table of some IEEE Standards for **Fiber-Optic cables**.

|Informal Name|IEEE Standard|Speed|Cable Type|Maximum Length|
|---|---|---|---|---|
|1000BASE-LX|802.3z|1 Gbps|M or S|550 m (M)/5 km (S)|
|10GBASE-SR|802.3ae|10 Gbps|M|400m|
|10GBASE-LR|802.3ae|10 Gbps|S|10 km|
|10GBASE-ER|802.3ae|10 Gbps|S|30 km|


# Copper UTP cable
## RJ-45
![[RJ-45 port.png]]

Lots of devices connect to the wired network using **RJ-45** ports (RJ means Registered Jack). 

![[RJ-45 Connector.png]]
The RJ-45 connector is used on the end of a **copper Ethernet cable**.

The copper cables used in Ethernet standards are **Unshielded Twisted Pair**.

**Unshielded** means that the wires have no metallic shield, which can make them vulnerable to **electrical interference** and easy to tap into.

The **twist** protect against **electromagnetic interference (EMI)**. 

There are 4 pair of cables twisted together in one UTP cable, that makes 8 wires in total. RJ-45 connector have 8 pins, each pin connects to one wire.

Before we start, we need to know that different network devices use different pin pairs to Transmit or Receive data.

![[Device pin pairs.png]]

## Pinouts for 10BASE-T & 100BASE-T
### Straight-through Cable

To connect devices that transmit and receive on opposite pin pairs, we use straight-through cable.

![[Straight-through full duplex.png]]

Just like that, both devices send and receive data at the same time, and there are no collisions because they use separate wires to transmit and receive data, which is known as **Full Duplex Transmission**.

However, we **cannot** use straight-through cable to connect devices that transmit or receive on the same pin pair.

![[Straight-through failure.png]]
### Crossover cable

To deal with the problem, we use crossover cable.

![[Crossover cable.png]]

However, this classification is an outdated technology. We need to know that because you might be questioned in the CCNA test.

![[Q599.png]]

### Auto MDI-X

Newer network devices include a feature called **Auto MDI-X**.

Auto MDI-X allows devices to automatically detect which pins their neighbor is transmitting data on and then adjust which pins they use to transmit and receive data.

So, unless we are working with a network equipment that is quite old, we don't really have to worry about straight-through or crossover cables.

![[Auto MDI-X.png]]

## Pinouts for 1000BASE-T & 10GBASE-T

![[1000BAST-T.png]]

In addition to using all four pairs of wires, in 1000BASE-T and 10GBAST-T, each pair is **[Bidirectional](https://dictionary.cambridge.org/dictionary/english/bidirectional?q=Bidirectional)**, which mean each pair isn't dedicated specifically to transmitting or receiving data.

This is a part of the reason that they can operate at much faster speeds.








## ISO/IEC 11801 & TIA/EIA-568

In the CCNA test, you might be questioned like this:
![[Cat 5e and Cat 6 Similarities.png]]

These terms, Cat5e and Cat6, define the copper cable specifications in other standards. 

|Specification|Category 5e (Cat5e)|Category 6 (Cat6)|
|---|---|---|
|Governing TIA Standard|ANSI/TIA-568.2-D|ANSI/TIA-568.2-D|
|Governing ISO Standard|ISO/IEC 11801 (Class D)|ISO/IEC 11801 (Class E)|
|Maximum Bandwidth (Frequency)|Up to 100 MHz|Up to 250 MHz|
|Max Data Rate (**Full Length - 100m**)|**1 Gbps** (Gigabit Ethernet)|**1 Gbps** (Gigabit Ethernet)|
|Max Data Rate (Short Run)|2.5 Gbps / 5 Gbps (depending on run)|10 Gbps (up to **55 meters**)|
|Physical Construction Note|Usually unshielded twisted pairs (UTP) without internal separator|Tighter twists; often includes a physical internal cross/spline separator|

IEEE 802.3 defines the "traffic rules", but how fast you can actually transmit or receive data depends on the "road", these ISO/IEC or EIA copper cable parameters.

> [How to understand the relationship between IEEE and these standards](https://zhuanlan.zhihu.com/p/2041217262988911140)



  

