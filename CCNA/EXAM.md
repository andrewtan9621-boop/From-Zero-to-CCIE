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
    
    Run `show ip nat translations` on R2 to verify dynamic translations are populated during the ping.
    
      
    

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

  

Plaintext

```
ntp master 1
```

**R2 Configuration (NTP Client):**

  

Plaintext

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
username root privilege 15 secret s3cret
!
line vty 0 4
 login local
 transport input ssh
```

- **Verification (from R1):**
    
      
    
    Plaintext
    
    ```
    ssh -l root 10.1.3.11
    ```
    
    Verify successful prompt for password `s3cret` and successful interactive shell access.