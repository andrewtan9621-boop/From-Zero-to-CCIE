Ping is a network utility that is used to test reachability, for example, to test if two computers can reach each other.

It measures the round-trip time.

Like ARP, ping uses two messages:

|ICMP Echo Request|ICMP Echo Reply|
|---|---|

**Internet Control Message Protocol (ICMP)** is a Layer 3, network Layer, protocol used by devices to send error messages and operational information about IP packet delivery.

Note that the PC won’t broadcast the ICMP Echo request, it is sent to a specific host. 

So, the PC has to know the MAC address of the destination host, which is why **ARP must be use first**.

The command to use ping is

```
PC1#ping 192.168.0.1
```

![[Ping 1.png]]

By default, a ping in Cisco IOS sends 5 ICMP echo requests, and you should get 5 echo replies back.

The default size of each ping is 100 bytes.

Notice the ".!!!!" mark. ‘.’ indicates a failed ping, ‘!’ indicates a successful ping.

Why did that first ping fail? That’s because of ARP.

PC1 didn’t know the destination MAC address, so it had to use ARP, and in that time the first ping failed. 

After PC1 learned the MAC address, the pings succeeded.

