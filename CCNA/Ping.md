Ping is a network utility that is used to test reachability, for example, to test if two computers can reach each other.

It measures the round-trip time.

Like [[Layer 2 Ethernet LAN Switching#Address Resolution Protocol|ARP]], ping uses two messages:

|ICMP Echo Request|ICMP Echo Reply|
|---|---|

However the PC won’t broadcast the ICMP Echo request, it is sent to a specific host. 

So, the PC has to know the MAC address of the destination host, which is why **ARP must be use first**.

The command to use ping is

```
PC1#ping 192.168.0.1
```

![[Ping 1.png]]

By default