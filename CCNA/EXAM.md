# Q770

### **Task 1: Dynamic One-to-One NAT on R2**

**R2 Configuration:**


```
ip access-list standard XLATE
 permit any
!
ip nat pool test_pool 10.10.10.1 10.10.10.254 netmask 255.255.255.0
ip nat inside source list XLATE pool test_pool
!
interface Ethernet0/1
 ip nat inside
!
interface Ethernet0/0
 ip nat outside
```

- **Verification (on R3):**


 ```
 ping 192.168.100.1
 ``` 
- **Verification (how to confirm NAT step success on R2):**
 
Run `show ip nat translations` on R2 to verify dynamic translations are populate during the ping.

### **Task 2: Configure DHCP Client on R3**

**R3 Configuration:**

  

Plaintext

```
interface Ethernet0/2
 ip address dhcp
 no shutdown
```

- **Verification:**

Run `show ip interface brief Ethernet0/2` or `show dhcp lease` on R3 to verify that an IP address has been assigned dynamically.

### **Task 3: NTP Server and Client Configuration**

**R1 Configuration (NTP Server):**


```
ntp master 1
```

**R2 Configuration (NTP Client):**


```
ntp server 10.1.2.1
```

- **Verification:**
    
    Run `show ntp status` or `show ntp associations` on R2 to verify clock synchronization with master `10.1.2.1`.
    
      
    

### **Task 4: SSH Configuration on R3**

**R3 Configuration:**

  

Plaintext

```
ip domain-name lab.local
crypto key generate rsa modulus 2048
username root secret s3cret
!
line vty 0 4
 login local
 transport input ssh
```

- **Verification (from R1):**
  ```
 ssh -l root 10.1.3.11
  ```
  
Verify successful prompt for password `s3cret` and successful interactive shell access.

# Q787

Here is the step-by-step breakdown and configuration commands to complete this IPv4/IPv6 interface addressing lab.

  

### **1. Subnetting Calculations**

- **IPv4 Subnet Selection:**
    
      
    - Base Range: `192.168.180.0/24` with `/28` subnets (block size = 16).
        
          
        
    - First `/28` subnet: `192.168.180.0/28` (Prompt states this is **unavailable**).
        
          
        
    - **Next Usable `/28` Subnet:** `192.168.180.16/28`
        
          
        - Network ID: `192.168.180.16`
            
              
            
        - Broadcast ID: `192.168.180.31`
            
              
            
        - Subnet Mask: `255.255.255.240`
            
              
            
        - **First Usable Host (R1):** `192.168.180.17`
            
              
            
        - **Last Usable Host (R2):** `192.168.180.30`
            
              
            
- **IPv6 Subnet & Interface Addressing:**
    
      
    - Subnet: `2001:db8:acca::/64`
        
          
        
    - **R1 IPv6 Address:** `2001:db8:acca::1/64`
        
          
        
    - **R2 IPv6 Address:** `2001:db8:acca::2/64`
        
          
        

### **2. Router Configurations**

**R1 Configuration:**

```
interface Ethernet0/1
 ip address 192.168.180.17 255.255.255.240
 ipv6 address 2001:db8:acca::1/64
 no shutdown
```

**R2 Configuration:**

```
interface Ethernet0/1
 ip address 192.168.180.30 255.255.255.240
 ipv6 address 2001:db8:acca::2/64
 no shutdown
```

### **3. Verification Steps**

- **Verify IPv4 Reachability (from R1):**

    
    ```
    ping 192.168.180.30
    ```
    
    - _Verification Success Criteria:_ Ping response rate should show 100% success (`!!!!!`).
        
          
        
- **Verify IPv6 Reachability (from R1):**

    ```
    ping 2001:db8:acca::2
    ```
    
    - _Verification Success Criteria:_ Ping response rate should show 100% success (`!!!!!`).

![[q200.png]]