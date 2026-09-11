# CLI and GUI

Cisco IOS is the operating system used on Cisco devices.

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

## User Authorization

There are three user mode.

|Prompt| Mode|
|---|---|
|Router>|user EXEC mode|
|Router#|privileged EXEC mode|
|Router(config)#|global configuration mode|

```
Router>enable
Router#configure terminal
Router(config)#
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

````
Router>en
Router#exit
Router>e   # Ambiguous
```