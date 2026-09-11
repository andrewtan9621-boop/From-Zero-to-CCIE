This is the fundamental knowledge about how to configure a Cisco [[Layer 2 Ethernet LAN Switching|Switch]] or [[Router|Router]].

# CLI and GUI

Cisco IOS is the **operating system** used on Cisco devices.

CLI means Command-Line Interface.

GUI means Graphical User Interface.

![[CLI & GUI.png]]

# Console Port

In any case, when you first configure a device, you have to connect to the console port.

![[Console port.png]]

![[Figure 4-3.png]]

## Rollover Cable

![[Rollover cable.png]]

Notice that one end of rollover cable has an RJ45 connector, the other end is DB9 connector which is plugged into a **serial port**.

Most laptops these days no longer have a serial port. You probably need an adapter to connect to a USB port on your laptop.

## Default Cisco Console Setting 

![[Emulator about console port.png]]

|Parameter | Setting | |
|---|---|---|
|Baud rate| 9600|
|Date bits| 8|
|Stop bits| 1|
|Parity| None| Parity is used to detect errors|
|Flow control| None| Control the flow of data from transmitter to receiver|

You don't have to worry about the details for the CCNA exam.

# CLI Command List

I recommend you to learn the function of each command practically. Follow videos in the end.

## User Mode

There are three user mode.

|Prompt| Mode|
|---|---|
|Router>|user EXEC mode|
|Router#|privileged EXEC mode|
|Router(config)#|global configuration mode|

```
Router>enable
password:   #need to be set
Router#configure terminal
Router(config)#
```
## Set Pass word
```
#they are case-sensative

Router(config)#enable 11Aa   
#to be stored in plain text

Router(config)#enable secret 22Aa 
#always MD5 encrypted, more secure, higher priority

Router(config)#enable algorithm-type scrypt secret 33Aa
#most secure

```
Notice that, the device will ignore the # enable *password* command if the # enable secret command is executed. We need to use *22Aa* to enter the privileged EXEC mode.

Remember the strongest password setting method, you might be questioned in the CCNA exam like this:

![[Strongest Password.png]]

## Check and Save Configuration Files

There are two separate configuration files kept on the device at once.

**Running-config**: the current, active configuration file on the device. As you enter commands in the CLI, you edit the active configuration.

**Startup-config**: the configuration file that will be loaded upon restart of the device.

When we first configure a device, the **default configuration** will be loaded. 
If we save running-config, the startup-config will exist and be loaded when we reboot the device.

```
#check configurations
Router#show running-config
Router#show startup-config

#save configurations
Router#write
Router#write memory
Router#copy running-config startup-config
```
## service password encryption

```
Router(config)#enable 11Aa3$@
Router(config)#service password encryption
```

This command prevents the password from being displayed in **plaintext** in the configuration files.

![[Service password encryption.png]]


## no

We add "no" as a prompt in front of a command to remove it.

```
Switch(config-if)#no switchport mode trunk
```

## do

```
Router#show running-config
Router(configre)#do show running-config
```

## ?

Use a question mark ? to view the available command.

```
Router>?
```

## Press Tab Key 

Press Tab key to automatically complete the command word.

```
Router>en   #press Tab
Router>enable
```

## Abbreviation without Ambiguous

```
Router>en
Router#exit
Router>e   # Ambiguous 

Router>en
Router#conf t
Router(config)#do sh run
```

# References

>[Jeremy's IT Lab CCNA Day 4](https://www.youtube.com/watch?v=IYbtai7Nu2g&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=11)