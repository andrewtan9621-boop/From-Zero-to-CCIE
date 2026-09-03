|Layer|OSI|TCP-IP|PDUs (Protocol Data Units)|Related network device or protocol|
|---|---|---|---|---|
|7|Application||||
|6|Presentation||||
|5|Session|Application||HTTP & HTTPS|
|4|Transport|Transport|Segment (Data+L4 header)|TCP & UDP|
|3|Network|Network|Packet (Segment+L3 header)|Routers|
|2|Datalink|Datalink|Frame (L2 trailer+Packet+L2 header)|Switches|
|1|Physical|Physical|Bits|UTP cable & Fiber Optic cable|

![[Figure 1-14.png]]
# Layer 5 Application: HTTP overview
Now, you open a web browser in your computer. Type in your question, and click a hyperlink. However, what you see is not actually stored on your local storage. Your web browser have to control your device to send a request to a remote sever for retrieving the web page.

![[Figure 1-5.png]]
![[Figure 1-6.png]]

To make the request for a web page and return the contents, the applications use the **Hypertext Transfer Protocol (HTTP)**. 
The full version of most web addresses—also called **Uniform Resource Locators (URL)** or **Universal Resource Identifiers (URI)**—begins with the letters * http*, which means that HTTP is used to transfer the web pages.

# Layer 4 Transport: TCP and UDP overview

A computer device is like an office building. Many applications work in it. The function of the transport port layer is to give a room number to deliverymen of network layer, which helps packets being transported to a correct room when all applications work concurrently.

**The Office Building = The Device / Host (IP Address)** 

The Network Layer delivers the package to the correct physical building (device) using the street address (IP address).
    
**The Room Number = The Port Number (Transport Layer)** 

Once the delivery driver arrives at the building, they use the room number (Port Number) to take the package to the exact office inside.

The two most commonly used transport layer protocols are the **Transmission Control Protocol (TCP)** and the **User Datagram Protocol (UDP)**

# Layer 3 Network: Internet Protocol (IP)

The **Internet Protocol** provides several features, most importantly, addressing and routing.

Imagine that you just wrote a letter to a friend on the other side of the country. You addressed the envelopes and put on the stamp, so it is ready to give to the postal service.

The postal service sends the letter to another post office, then another, and so on, until the letter gets delivered across the country. At each post office, the postal service must process the letter and choose where to send it next. To make it all work, the postal service has regular routes.

Router works in the same way of each post office: check the destination **IP address**, look up a table, and determine which route is used to transport the letter to the next router.

# Layer 2 & 1 Datalink and Physical

If you want to tell something to your neighbor, you probably won't write a letter. Instead, you just need to know which house is your neighbor's home, and choose a good time to visit him. That's what happened in these two layers.

The two work together quite closely; in fact, some standards define both the data-link and physical layer functions. **The physical layer** defines the cabling and energy (for example, electrical signals) that flow over the cables. **The datalink layer** provides methods for **LAN switching**, which means communication between directly Ethernet-connected devices. 


# Adjacent Layer Interactions

Both the encapsulation and de-encapsulation process are examples of **[adjacent](https://dictionary.cambridge.org/dictionary/english-chinese-simplified/adjacent)-layer interaction**, which are interactions between the different layers of the OSI model.

Data is processed through the OSI stack, each layer adding something to the original data. This is called **Encapsulation**, because the original data is encapsulated inside this additional information which is added on. 

By the time the message reaches the physical layer, it is electrical signals on a wire and is sent to the neighboring system.

Then the neighboring system performs the opposite process, the additions of each layer are [stripped](https://dictionary.cambridge.org/dictionary/english-chinese-traditional/strip) off until the data reaches the application layer. This process is called **De-encapsulation**. 
![[Figure 1-12.png]]
![[Figure 1-13.png]]

# Same Layer Interactions

**Same-layer interaction** refers to interaction between the same layer on different hosts. Communication between the application layers of the two different systems is called same-layer interaction. Same-layer interaction allows the application layer to perform its function.
![[Table 1-3.png]]

>[Jeremy's IT lab CCNA Day 3](https://www.youtube.com/watch?v=yM-XNq9ADlI&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=6)
>
>CCNA 200-301 Official Guidebook Volume1 Chapter 1