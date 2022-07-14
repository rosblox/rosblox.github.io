# ROSbloX interfaces

Three interfaces are available to transmit data to/from ROSbloX. First, a simple web interface can be used to visualize and/or download data from a ROSbloX. Second, the Python library, roslibpy, which enables data transmission to/from ROSbloX without installing ROS and is easy to integrate in Python scripts. And third, each ROSbloX can be found as ROS node by other ROS nodes in a network.  

Some networks do not allow the discovery of ROSbloX by their mDNS name, i.e. ROSbloX cannot be reached at rockpis.local. In that case their interfaces can be accessed by their IP address's, i.e. 10.99.10.99 if connected via USB and 10.99.12.99 if connected via Ethernet.

## Web Interface
To open a ROSbloX's web interface, a computer requires solely the [Chrome](https://www.google.com/chrome/) browser to be installed. After a ROSbloX has started (which can take up to a minute), its web interface is accessible at [http://rockpis.local](http://rockpis.local) in your Chrome browser. 

## roslibpy

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


## ROS

Each ROSbloX can be accessed as normal ROS node, e.g. it shows up when executing 
```
ros2 node list
ros2 topic list
```
We refer to the official ROS documentation how to communicate with ROS nodes in a network. Further resources and tutorials how to get started with ROS are xxx.   
