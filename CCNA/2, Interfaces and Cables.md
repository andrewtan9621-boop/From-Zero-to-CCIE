The [[Layer 1]], Physical Layer, sends and receives **bits** as electrical, optical, or radio signals over the medium.

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

**M** means **Multimode**. **S** means **Single-Mode**.

|Suffix|Meaning|
|---|---|
|LX| Long Wavelength|
|SR| Short Range|
|LR| Long Range|
|ER| Extended Range|


# Copper Cable Connections

## RJ-45 Connector
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

## 10BASE-T & 100BASE-T
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

#MDI-X

## 1000BASE-T & 10GBASE-T

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
|Max Data Rate (**Full Length - 100m**)|**1 Gbps** |**1 Gbps** |
|Max Data Rate (Short Run)|2.5 Gbps / 5 Gbps |10 Gbps (up to **55 meters**)|
|Physical Construction Note|Usually unshielded twisted pairs (UTP) without internal separator|Tighter twists; often includes a physical internal cross/spline separator|

IEEE 802.3 defines the "traffic rules", but how fast you can actually transmit or receive data depends on the "road", these ISO/IEC or EIA copper cable parameters.

> [How to understand the relationship between IEEE and these standards](https://zhuanlan.zhihu.com/p/2041217262988911140)

## Shield Twisted Pair (STP) Cable

![[STP Cable.png]]

**STP cable (Shielded Twisted Pair) uses metallic foil or braided mesh shielding around wire pairs to block electromagnetic interference (EMI) and reduce internal crosstalk.**

You might be asked to compare them in the exam, like this:

![[Q600.png]]

Basically we need to know that STP cables are more expensive and can transmit signal over longer distances.

In the end, notice that **each type of cable requires its corresponding RJ45 connector** in practical works.

# Fiber-Optic Connections

## SFP Transceiver

![[SFP Transceiver.png]]

SFP means Small Form-Factor Pluggable.

Like RJ45, the SFP transceiver is used on the end of a **fiber optic cable**.

Notice that we can use SFP on copper cables by using a copper SFP transceiver module or a Direct Attach Copper (DAC) cable.

#SFP 

## Fiber Optic Cable

Rather than a electrical signal over the copper wiring, these cable send light over glass fibers.

![[Fiber transmit and receive.png]]

Fiber optic cables also use separate cables to transmit and receive, like this.

![[Figure 2-15.png]]

A fiber optic cable consists of 4 or 5 layers:

|Layer | Function |
|---|---|
|Fiber glass core | Light is transmitted down this core|
|Cladding | Reflects the light|
|Buffer | Protects the fiberglass from breaking|
|Strengthener and Out Jacket| Enhance the protection|

### Multimode Fiber

![[Multimode Fiber.png]]

In multimode fiber, the core, the actual glass fiber, is wider than single mode fiber.

This wider core allows multiple angles, known as modes, of light waves to enter the fiber glass core. However, this causes **attenuation** over long distances.

Therefore, multimode fiber allows longer cable than UTP, but shorter than single-mode fiber.

Multimode fiber is cheaper than single-mode fiber(due to cheaper LED-based SFP transmitters).

#Multimode

### Single-mode Fiber

![[Single mode fiber cable.png]]

In single-mode fiber, core [diameter](https://dictionary.cambridge.org/dictionary/english-chinese-traditional/diameter) is [narrower](https://dictionary.cambridge.org/dictionary/english-chinese-traditional/narrow?q=narrower) than multimode fiber.

Light enters at a single angle from a laser-based transmitter.

Single-mode fiber allows longer cables than both UTP and multimode fiber.

Single-mode fiber is more expensive than multimode fiber (due to more expensive laser-based SFP transmitters).

#Singlemode

### Fiber Connector

![[Fiber connector.png]]

#### SC connector

In modern optic networks, SC connectors might be very common. You could see them on the **Optical Network Terminal (ONT)** in your home.

The color blue distinguishes it as an **Ultra Physical Contact (UPC)"**, which is used to transmit **digital signals**, such as Ethernet frames.
![[UPC.png]]

And then, there is a green one, **Angled Physical Contact (APC)**, which is used to transmit **analog signals**, such as cable TV signal.
![[APC.png]]

#### LC connector

![[LC.png]] 

LC has a smaller size to alleviate the shortage of space in Internet Data Center (IDC), which makes them the standard interfaces of SFP modules. And then, blue and green distinguish between two different types.  

In the CCNA exam, you might be questioned about the SC to LC adapter.


# Comparison between Copper and Fiber-Optic Cable 

In the CCNA test, you will be questioned to compare these two types of cables.

This a summary of what we mentioned.

![[Comparison.png]]

In addition, fiber-optic cables are more fragile than copper cables.

# References

>[Jeremy's IT Lab CCNA Day 2](https://www.youtube.com/watch?v=ieTH5lVhNaY&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=4)
>
>CCNA 200-301 Official Guidebook Volume1 Chapter 2
>
>[蓝色上网、绿色看电视？光猫上的光纤接头一次看懂｜SC/UPC、SC/APC、热熔冷接、FTTR_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1c6HX6GEEj/?spm_id_from=333.1007.top_right_bar_window_history.content.click&vd_source=fac47894cc514f77fd5981bcde0f5ead)
>
>[光纤接头进化史下集：FC 拧、ST 卡、SC 推、LC 减半，TOSLINK 光纤音频、机房 SFP/LC/MPO、光猫棒一次理清_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1KJpn68Ejz/?spm_id_from=333.1387.homepage.video_card.click&vd_source=fac47894cc514f77fd5981bcde0f5ead)