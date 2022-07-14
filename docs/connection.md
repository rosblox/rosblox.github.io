# Connecting to ROSbloX

ROSbloX can be connected to computers which run Windows, MacOS or Linux via USB-C or Ethernet. Note, ROSbloX do not require any installation of ROS on a computer.  


## Connecting to ROSbloX via USB

The USB port of a ROSbloX is configured such that it appears to a connecting computer as a network adapter. It runs a DHCP server on the USB interface and automatically assigns an IP address to the connecting computer. When connected via USB, the ROSBloX is accessible via its static IP address, 10.99.0.1. 

## Connecting to ROSbloX via Ethernet 

Each ROSbloX's Ethernet interface has two IP addresses assigned to it. One static which is set on the ROSbloX itself and one dynamic which waits for a DHCP lease.

### Dynamic IP Adress (from a DHCP Server)

The dynamic IP address of a ROSbloX is assigned to it by a DHCP server in the network. To access a ROSbloX via its dynamic IP address, the IP address has to retrieved from the DHCP server.

### Static IP Adress

Each ROSbloX ships with the same static IP address, 10.99.1.2, with subnet mask 255.255.255.0. To access a ROSbloX via their static IP address, ensure the computer's connected Ethernet interface has a static IP address in the same subnet, e.g. 10.99.1.1.  

Note, this can lead to conflicts if you connect multiple ROSbloX to the same network. See [Changing a ROSbloX network configuration](#changing-a-rosblox-network-configuration), for instructions how to change a ROSbloX network configuration.

## Checking connectivity

Before receiving data from a ROSbloX, ensure that the ROSbloX is connected by pinging it:
```
ping rosblox.local # Resolves correct IP address automatically
```

Some networks prohibit discovery of ROSbloX by their mDNS name, i.e. it cannot be reached via ```rosblox.local```. In that case a ROSbloX can be reached via its IP address:
```
ping 10.99.10.99 # If connected via USB
ping 10.99.11.99 # If connected via Ethernet (static IP address)
```

More information on how to use the ping command can be found [here](https://www.siteground.com/kb/how_to_perform_ping_checks_in_windows_linux_and_mac_os/).  If the ROSbloX is not reachable by either of the commands, the network setup does not work properly. Please leave some feedback in our feedback form: [ROSbloX Feedback](https://forms.gle/vUeeocDE7jSQKdCc7)   