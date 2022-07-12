# The ROSbloX documentation

ROSbloX are modules to discover the Robot Operating System (ROS).

Join us on Slack: [ROSbloX Workspace](https://join.slack.com/t/rosblox/shared_invite/zt-1c6ifc24n-OswQtNwORkq588QPNZ2KoA)  
Follow us on Twitter: [ROSblox (@xploros)](https://twitter.com/xploros)

## About

The Robot Operating System (ROS), [https://www.ros.org/](https://www.ros.org/), is rapidly becoming a de facto standard for writing interoperable and reusable robot software. The interoperability and reusability of ROS software come at the price of an increased sofware complexity. Getting started with ROS can be particularly challenging for developers with a primary background in mechanical or electrical engineering and not sofware engineering.  

ROSbloX are modules to explore various sensors and actuators and to discover the capabilities of ROS with minimal prior knowledge. Each ROSbloX implements a sensor or an actuator, is equipped with multiple interfaces to communicate with other computers and simple interfaces,  i.e. a web interface, a python library, and native ROS, to transmit data. 

## Requirements

ROSbloX function with computers which run Windows, MacOS or Linux. To open a ROSbloX's web interface, a computer requires solely the [Chrome](https://www.google.com/chrome/) browser to be installed. Note, ROSbloX do not require an installation of ROS on the computer.

## Connecting to ROSbloX

ROSbloX can be connected via USB-C or Ethernet.

### Connecting to ROSbloX via USB

The USB port of ROSbloX is configured such that the ROSbloX appears on your computer as a network adapter. When connected via USB, the ROSBloX is accessible via the static IP address, [10.99.10.99/24]. The ROSbloX runs a DHCP server on the USB interface and automatically assigns an IP address to your computer. 

### Connecting to ROSbloX via Ethernet 

Each ROSbloX's Ethernet interface has two IP addresses assigned to it. One static which is set on the ROSbloX itself and one dynamic which waits for a DHCP lease.

#### Dynamic IP Adress from a DHCP Server 

The dynamic IP address of a ROSbloX is assigned to it by a DHCP server. To access a ROSbloX via its dynamic IP address, the IP address is found on the DHCP server.

#### Static IP Adress

To access a ROSbloX via their static IP address, make sure the computer's connected Ethernet interface has a static IP address in the same subnet. 
Each ROSbloX ships with the same static IP address, [10.99.11.99/24]. Note, this can lead to conflicts if you connect multiple ROSbloX to the same network. [Custom foo description](#changing-a-rosblox-network-configuration)

## Interfacing with ROSbloX

Three interfaces can be used to transmit data to/from ROSBloX. A simple web interface is accessible without installation of any additional software except a webbrowser. The webinterface can be used to visualize and/or download data from a ROSbloX. The Python library, roslibpy, enables data transmission to/from ROSbloX without installing ROS and is easy to integrate Python scripts. Finally, each ROSbloX can be found as ROS node by other ROS nodes in a network.

### Web Interface

After a ROSbloX has started (it can take up to a minute), its web interface is accessible at [http://rockpis.local] in your Chrome browser. Some networks do not allow the discovery of ROSBloX by their mDNS name, i.e. they cannot be reached at [http://rockpis.local]. In that case their web interface can be accessed at their IP address's, i.e. [http://10.99.10.99] if connected via USB and [http://10.99.12.99] if connected via Ethernet.

### roslibpy

To transmit data to/from a ROSblox in a Python script, the roslibpy can be used. Install the library with pip install roslibpy.
<todo show example in 5 lines how to receive data>

### ROS

Each ROSbloX can be accessed as normal ROS node, e.g. it shows up when executing ros2 topic list. We refer to the official ROS documentation how to communicate with ROS nodes in a network. Further resources and tutorials how to get started with ROS are xxx.  


## Open Architecture

ROSblox are open. Login to a ROSbloX via SSH.  

Username: rock  
Password: rock  

### Changing a ROSbloX network configuration

The ROSbloX network interfaces are configured in /etc/netplan/01-net.cfg. 
We refer to netplan.io for further instructions how to modify its network configuration.
