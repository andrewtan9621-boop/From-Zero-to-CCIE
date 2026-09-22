# Q769
![[Q769.png]]
![[Q769-1.png]]

``` 
Task1
SW1(config)# vlan 12
SW1(config-vlan)# name Compute
SW1(config)# vlan 34
SW1(config-vlan)# name Telephony

SW2(config)# vlan 12
SW2(config-vlan)# name Compute
```

``` 
Task2
SW2# show vlan brief
SW2(config)# interface Ethernet0/1
SW2(config-if)# switchport mode access
SW2(config-if)# switchport access vlan <VLAN_ID_OF_AVAILABLE>
SW2(config-if)# exit
```

``` 
Task3
SW1(config)# interface Ethernet0/0
SW1(config-if)# switchport mode access
SW1(config-if)# switchport access vlan 12

SW2(config)# interface Ethernet0/0
SW2(config-if)# switchport mode access
SW2(config-if)# switchport access vlan 12
```


``` 
Task4
SW1(config)# interface Ethernet0/1
SW1(config-if)# switchport mode access
SW1(config-if)# switchport access vlan 12
SW1(config-if)# switchport voice vlan 34
```

# Q770
![[Q770.png]]
![[Q770-1.png]]

``` 
Task1
##
R2(config)# ip access-list standard XLATE
R2(config-std-nacl)# permit 10.2.3.0 0.0.0.255
R2(config-std-nacl)# exit

R2(config)# ip nat pool test_pool 10.10.10.1 10.10.10.254 netmask 255.255.255.0
##

R2(config)# ip nat inside source list XLATE pool test_pool

R2(config)# interface Ethernet0/1
R2(config-if)# ip nat inside

R2(config)# interface Ethernet0/0
R2(config-if)# ip nat outside

R3# ping 192.168.100.1
```

``` 
Task2
R3(config)# interface Ethernet0/2
R3(config-if)# ip address dhcp
R3(config-if)# no shutdown
```

``` 
Task3
R1(config)# ntp master 1
R2(config)# ntp server 10.1.2.1

##show ntp status
```

``` 
Task4
R3(config)# crypto key generate rsa modulus 2048
R3(config)# username root secret s3cret

R3(config)# line vty 0 4
R3(config-line)# transport input ssh
R3(config-line)# login local

## R1# ssh -l root 10.1.3.11
```

# Q787
![[Q787.png]]
![[Q787-1.png]]

```
R1(config)# interface Ethernet0/1
R1(config-if)# ip address 192.168.180.17 255.255.255.240
R1(config-if)# ipv6 address 2001:db8:acca::1/64
R1(config-if)# no shutdown

R2(config)# interface Ethernet0/1
R2(config-if)# ip address 192.168.180.30 255.255.255.240
R2(config-if)# ipv6 address 2001:db8:acca::2/64
R2(config-if)# no shutdown
```

# Q788
![[Q788.png]]
![[Q788-1.png]]

```
Sw1(config)# vlan 303
Sw1(config-vlan)# name FINANCE
Sw1(config-vlan)# exit

Sw1(config)# interface Ethernet0/1
Sw1(config-if)# switchport mode access
Sw1(config-if)# switchport access vlan 303
Sw1(config-if)# exit
```

```
Sw2(config)# vlan 202
Sw2(config-vlan)# name MARKETING
Sw2(config)# vlan 303
Sw2(config-vlan)# name FINANCE
Sw1(config-vlan)# exit

Sw2(config)# interface Ethernet0/1
Sw2(config-if)# switchport mode access
Sw2(config-if)# switchport access vlan 202
Sw2(config-if)# exit
```

```
Sw3(config)# vlan 202
Sw3(config-vlan)# name MARKETING
Sw3(config)# vlan 303
Sw3(config-vlan)# name FINANCE
Sw3(config-vlan)# exit

Sw3(config)# interface Ethernet0/0
Sw3(config-if)# switchport mode access
Sw3(config-if)# switchport access vlan 202

Sw3(config)# interface Ethernet0/1
Sw3(config-if)# switchport mode access
Sw3(config-if)# switchport access vlan 303
Sw3(config-if)# exit
```

```
Task2
Sw1(config)# interface Ethernet0/2
Sw1(config-if)# switchport trunk encapsulation dot1q
Sw1(config-if)# switchport mode trunk
Sw1(config-if)# switchport trunk allowed vlan 303

Sw2(config)# interface Ethernet0/2
Sw2(config-if)# switchport trunk encapsulation dot1q
Sw2(config-if)# switchport mode trunk
Sw2(config-if)# switchport trunk allowed vlan 303
Sw2(config-if)# exit
```

```
Task3
Sw2(config)# interface Ethernet0/3
Sw2(config-if)# switchport trunk encapsulation dot1q
Sw2(config-if)# switchport mode trunk
Sw2(config-if)# switchport trunk allowed vlan 202,303

Sw3(config)# interface Ethernet0/3
Sw3(config-if)# switchport trunk encapsulation dot1q
Sw3(config-if)# switchport mode trunk
Sw3(config-if)# switchport trunk allowed vlan 202,303
Sw3(config-if)# exit
```

# Q806
![[Q806.png]]
![[Q806-1.png]]

```
Task1
R3(config)# ip route 192.168.1.1 255.255.255.255 209.165.200.229
R2(config)# ip route 192.168.1.1 255.255.255.255 209.165.200.225
R3# ping 192.168.1.1 source 2009.165.200.230
```

```
Task2
R2(config)# ip route 0.0.0.0 0.0.0.0 209.165.202.130
```

```
Task3
R2(config)# ipv6 unicast-routing
R2(config)# ipv6 route ::/0 2001:db8:abcd::2
```

# Q819
![[Q819.png]]
![[Q819-1.png]]
![[Q819-2.png]]
```
#show vlan brief
```

# Q836
![[attachments/Lab in exam/Q836.png]]
![[Q836-1.png]]
![[Q836-2.png]]

# Q837

```
R2(config)# ip route 192.168.0.0 255.255.255.0 Ethernet0/0 10.10.31.1

R2(config)# ip route 172.20.20.128 255.255.255.128 10.10.1.1
```

```
R1(config)# ip route 0.0.0.0 0.0.0.0 Ethernet0/0 10.10.254.3

R1(config)# ip route 192.168.0.0 255.255.255.0 Ethernet0/1 10.10.12.2
R1(config)# ip route 192.168.0.0 255.255.255.0 Ethernet0/2 10.10.12.130 2
```

# Q849

``` Task 1
R2(config)# ip access-list standard PUBNET
R2(config-std-nacl)# permit 10.2.3.0 0.0.0.255
R2(config-std-nacl)# permit 192.168.3.0 0.0.0.255

R2(config)# interface Ethernet0/1
R2(config-if)# ip nat inside

R2(config)# interface Ethernet0/0
R2(config-if)# ip nat outside
R2(config-if)# exit

R2(config)# ip nat inside source list PUBNET interface Ethernet0/0 overload
```

```Task2
R1# clock set 00:00:00 1 May 2018
R1# configure terminal
R1(config)# ntp master

R2(config)# ntp server 10.1.3.1
```

```Task3
R1(config)# ip dhcp excluded-address 10.1.3.1 10.1.3.10
R1(config)# ip dhcp pool NETPOOL
R1(dhcp-config)# network 10.1.3.0 255.255.255.0

R3(config)# interface Ethernet0/2
R3(config-if)# ip address dhcp
R3(config-if)# no shutdown
```

```Task 4
R3(config)# ip domain-name cisco.local
R3(config)# username netadmin privilege 15 password N3t4ccess
R3(config)# crypto key generate rsa
! When prompted for key modulus size, enter: 1024

R3(config)# line vty 0 4
R3(config-line)# login local
R3(config-line)# transport input ssh
R3(config-line)# exit

R1# ssh -l netadmin 10.1.3.11
```

# Q850
![[Q850.png]]
![[Q850-1.png]]

```Task1
R1(config)# router ospf 1
R1(config-router)# router-id 10.10.12.1

R2(config)# router ospf 1
R2(config-router)# router-id 10.10.12.2
```

```Task2
R2(config)# interface Ethernet0/0
R2(config-if)# ip ospf priority 255

R2(config)# interface Ethernet0/2
R2(config-if)# ip ospf priority 255

R1# clear ip ospf process
R2# clear ip ospf process
R3# clear ip ospf process
```

```Task3
R1(config)# router ospf 1
R1(config-router)# network 192.168.1.1 0.0.0.0 area 0

R2(config)# router ospf 1
R2(config-router)# network 192.168.2.2 0.0.0.0 area 0

R3(config)# router ospf 1
R3(config-router)# network 192.168.3.3 0.0.0.0 area 0
```

```Task4
R1(config)# int e0/1
R1(config-router)# ip ospf network point-to-point

R3(config)# int e0/
R3(config-router)# ip ospf network point-to-point
```

# Q851
![[Q851.png]]
![[Q851-1.png]]

```Task1
SW-2(config)# vlan 30
SW-2(config-vlan)# name SALES
```

```Task2
SW-2(config)# interface Ethernet0/2
SW-2(config-if)# switchport mode access
SW-2(config-if)# switchport access vlan 20
```

```Task3
SW-2(config)# interface Ethernet0/3
SW-2(config-if)# switchport mode access
SW-2(config-if)# switchport access vlan 30
```

```Task4
SW-1(config)# cdp run
SW-1(config)# interface Ethernet0/1
SW-1(config-if)#no cdp enable
SW-1(config)# interface Ethernet0/2
SW-1(config-if)#no cdp enable
##show cdp neighbors ##to check 
```


# Q852
![[Q852.png]]
![[Q852-1.png]]

```Task1
SW-1(config)# interface Ethernet0/0
SW-1(config-if)# switchport trunk allowed vlan 5,6
```

```Task2
SW-1(config)# interface Ethernet0/1
SW-1(config-if)# switchport trunk native vlan 77

SW-2(config)# interface Ethernet0/1
SW-2(config-if)# switchport trunk native vlan 77

```

```Task3
SW-2(config)# interface Ethernet0/2
SW-2(config-if)# switchport trunk allowed vlan 6
```

```Task4
SW-3(config)# interface range Ethernet0/0 - 1
SW-3(config-if-range)# channel-group 34 mode active

SW-4(config)# interface range Ethernet0/0 - 1
SW-4(config-if-range)# channel-group 34 mode passive
```

# Q853
![[Q853.png]]
![[Q853-1.png]]

```Task1
SW-1(config)# vlan 15
SW-1(config-vlan)# name OPS
```

```Task2
SW-2(config)# vlan 66
SW-2(config-vlan)# name ENGINEERING
```

```Task3
SW-1(config)# interface Ethernet0/1
SW-1(config-if)# switchport mode access
SW-1(config-if)# switchport access vlan 15
```

```Task4
SW-2(config)# interface Ethernet0/1
SW-2(config-if)# switchport mode access
SW-2(config-if)# switchport access vlan 66
```

```Task5
SW-1(config)# lldp run
SW-1(config)# interface Ethernet0/2
SW-1(config-if)# no cdp enable
SW-1(config-if)# lldp transmit
SW-1(config-if)# lldp receive

SW-1(config)# interface Ethernet0/0
SW-1(config-if)# cdp enable
SW-1(config-if)# no lldp transmit
SW-1(config-if)# no lldp receive

SW2 will be the same
```

# Q854
![[Q854.png]]
![[Q854-1.png]]

```
Sw101(config)# interface Ethernet0/0
Sw101(config-if)# ip address 172.25.8.1 255.255.248.0
Sw101(config-if)# ipv6 address 2001:DB8:0:20::/59 eui-64
Sw101(config-if)# no shutdown

Sw102(config)# interface Ethernet0/0
Sw102(config-if)# ip address 172.25.15.254 255.255.248.0
Sw102(config-if)# ipv6 address 2001:DB8:0:20::/59 eui-64
Sw102(config-if)# no shutdown
```

# Q857
![[Q857.png]]
![[Q857-1.png]]

```
Task1
Sw103(config)# username devnet privilege 15 algorithm-type sha256 secret access8cli
Sw103(config)# line vty 0 4
Sw103(config-line)# login local
Sw103(config-line)# transport input telnet
Sw103(config-line)# exit
```


```
Task2
R1(config)# ip access-list extended INTERNET_ACL
R1(config-ext-nacl)# permit tcp 172.16.0.0 0.0.255.255 any eq https
R1(config-ext-nacl)# permit tcp 172.16.101.0 0.0.0.255 any eq telnet
R1(config-ext-nacl)# deny ip any any log-input
R1(config-ext-nacl)# exit

R1(config)# interface Ethernet0/1
R1(config-if)# ip access-group INTERNET_ACL out
R1(config-if)# exit
```

```
Task3
Sw101(config)# ip dhcp snooping
Sw101(config)# ip dhcp snooping vlan 101
Sw101(config)# no ip dhcp snooping information option
Sw101(config)# ip dhcp snooping verify mac-address
```

# Q858 
![[Q858.png]]
![[Q858-1.png]]

```
Task1
Sw101(config)# username support privilege 15 secret max2learn
Sw101(config)# line vty 0 4
Sw101(config-line)# login local
Sw101(config-line)# transport input telnet
Sw101(config-line)# exit
```

```
Task2
Sw101(config)# ip access-list extended ENT_ACL
Sw101(config-ext-nacl)# deny icmp host 192.168.200.10 host 192.168.100.10 echo
Sw101(config-ext-nacl)# permit tcp host 192.168.200.10 any eq 23
Sw101(config-ext-nacl)# deny tcp any any eq 23
Sw101(config-ext-nacl)# permit ip any any
Sw101(config-ext-nacl)# exit

Sw101(config)# interface Vlan200
Sw101(config-if)# ip access-group ENT_ACL in
Sw101(config-if)# exit
```

```
Task3
Sw102(config)# interface Ethernet0/0
Sw102(config-if)# switchport port-security
Sw102(config-if)# switchport port-security maximum 4
Sw102(config-if)# switchport port-security violation protect
Sw102(config-if)# switchport port-security mac-address sticky
Sw102(config-if)# exit
```

# Q882
![[Q882.png]]
![[Q882-1.png]]
![[Q882-2.png]]

# Q883
![[Q883.png]]
![[Q883-1.png]]
![[Q883-2.png]]