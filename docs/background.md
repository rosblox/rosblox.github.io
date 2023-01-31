# Further Reading

## Changing a ROSbloX network configuration

The ROSbloX network interfaces are configured with [Netplan](https://netplan.io/). The network configuration file is located in the ROSbloX file system under /etc/netplan/01-net.cfg.


## Access to ROSbloX

ROSblox are open. Login to a ROSbloX via SSH.  

Username: rock  
Password: rock  


## Checking connectivity

Before receiving data from a ROSbloX, ensure that the ROSbloX is connected by pinging it:
```
ping rosblox.local # Resolves correct IP address automatically
```

Some networks prohibit discovery of ROSbloX by their mDNS name, i.e. it cannot be reached via ```rosblox.local```. In that case a ROSbloX can be reached via its IP address:
```
ping 10.99.11.1 # If connected via USB
ping 10.99.1.XXX # If connected via Ethernet (static IP address)
```

More information on how to use the ping command can be found [here](https://www.siteground.com/kb/how_to_perform_ping_checks_in_windows_linux_and_mac_os/).  If the ROSbloX is not reachable by either of the commands, the network setup does not work properly.


