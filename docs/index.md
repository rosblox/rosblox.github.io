# The ROSbloX documentation

ROSbloX are modules to discover the Robot Operating System (ROS).

Join us on Slack: [ROSbloX Workspace](https://join.slack.com/t/rosblox/shared_invite/zt-1c6ifc24n-OswQtNwORkq588QPNZ2KoA)  
Follow us on Twitter: [ROSbloX (@xploros)](https://twitter.com/xploros)  
Subscribe to our Youtube channel: [ROSbloX](https://www.youtube.com/channel/UC8t8kygP_QODOw7MCxGZJVg)  
Leave feedback in our Google form: [ROSbloX Feedback](https://forms.gle/vUeeocDE7jSQKdCc7)

## About ROSbloX

The Robot Operating System (ROS), [https://www.ros.org/](https://www.ros.org/), is rapidly becoming a de facto standard for writing interoperable and reusable robot software. The interoperability and reusability of ROS software come at the price of an increased sofware complexity. Getting started with ROS is complex, especially for developers with backgrounds other than sofware engineering.  

ROSbloX are modules to explore the functionality of various sensors and actuators and to discover the capabilities of ROS with minimal prior knowledge. Each ROSbloX implements a sensor or an actuator, is equipped with multiple communication interfaces to connect to computers and simple user interfaces, namely a web interface, a python library, and native ROS, to transmit data.  

The ROSbloX project has just started. We greatly appreciate your inputs through our amazing [ROsbloX Feedback](https://forms.gle/vUeeocDE7jSQKdCc7) form to further develop the project. 

## Requirements

ROSbloX function with computers which run Windows, MacOS or Linux. 
Note, ROSbloX do not require any installation of ROS on a computer.  

## Connecting to ROSbloX

ROSbloX can be connected via USB-C or Ethernet.

### Connecting to ROSbloX via USB

The USB port of a ROSbloX is configured such that it appears to a connecting computer as a network adapter. It runs a DHCP server on the USB interface and automatically assigns an IP address to the connecting computer. When connected via USB, the ROSBloX is accessible via its static IP address, 10.99.10.99/24. 

### Connecting to ROSbloX via Ethernet 

Each ROSbloX's Ethernet interface has two IP addresses assigned to it. One static which is set on the ROSbloX itself and one dynamic which waits for a DHCP lease.

#### Dynamic IP Adress from a DHCP Server 

The dynamic IP address of a ROSbloX is assigned to it by a DHCP server in the network. To access a ROSbloX via its dynamic IP address, the IP address has to retrieved from the DHCP server.

#### Static IP Adress

Each ROSbloX ships with the same static IP address, 10.99.11.99/24. To access a ROSbloX via their static IP address, ensure the computer's connected Ethernet interface has a static IP address in the same subnet. Note, this can lead to conflicts if you connect multiple ROSbloX to the same network. See [Changing a ROSbloX network configuration](#changing-a-rosblox-network-configuration), for instructions how to change a ROSbloX network configuration.

## Interfacing with ROSbloX

Three interfaces are available to transmit data to/from ROSbloX. First, a simple web interface can be used to visualize and/or download data from a ROSbloX. Second, the Python library, roslibpy, which enables data transmission to/from ROSbloX without installing ROS and is easy to integrate in Python scripts. And third, each ROSbloX can be found as ROS node by other ROS nodes in a network.  

Some networks do not allow the discovery of ROSbloX by their mDNS name, i.e. ROSbloX cannot be reached at rockpis.local. In that case their interfaces can be accessed by their IP address's, i.e. 10.99.10.99 if connected via USB and 10.99.12.99 if connected via Ethernet.

### Web Interface
To open a ROSbloX's web interface, a computer requires solely the [Chrome](https://www.google.com/chrome/) browser to be installed. After a ROSbloX has started (which can take up to a minute), its web interface is accessible at [http://rockpis.local](http://rockpis.local) in your Chrome browser. 

### roslibpy

To transmit data to/from a ROSblox in a Python script, the roslibpy can be used. Install the library with 
```
pip install roslibpy
```
Afterwards, you can run the following lines in a Python shell to receive data from your ORSbloX.

```
from __future__ import print_function
import roslibpy

client = roslibpy.Ros(host='rockpis.local', port=9090)
client.run()

listener = roslibpy.Topic(client, '/topic', 'std_msgs/Float32')
listener.subscribe(lambda message: print(message))

try:
    while True:
        pass
except KeyboardInterrupt:
    client.terminate()
```


### ROS

Each ROSbloX can be accessed as normal ROS node, e.g. it shows up when executing 
```
ros2 node list
ros2 topic list
```
We refer to the official ROS documentation how to communicate with ROS nodes in a network. Further resources and tutorials how to get started with ROS are xxx.  

## Open Architecture

ROSblox are open. Login to a ROSbloX via SSH.  

Username: rock  
Password: rock  

### Changing a ROSbloX network configuration

The ROSbloX network interfaces are configured in /etc/netplan/01-net.cfg. 
We refer to netplan.io for further instructions how to modify its network configuration.

### Updating a ROSbloX

The ROSbloX can be updated by executiong docker compose pull in the the main repository in the home folder.