# Single ROS master Setup
To setup Single ROS Master we just need ROS_IP and ROS_MASTER_URI.
### Single ros master setup at Sender side 
At sender side ROS_IP and ROS_MASTER_URI is same. I have setup it by capturing IP address on interface ***eth0*** 
```sh
value=$(ip a s eth0 | egrep -o 'inet [0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' | cut -d' ' -f2)
export ROS_MASTER_URI=http://$value:11311
export ROS_IP=$value
```
> Make sure to change <eth0> with your network interface, which you want to use for ROS_IP.
## Single ros master ssetup at receive side
At receiver side ROS_IP should be the IP address of receiver machine but ROS_MASTER_URI must be the IP address of the machine on which ROS Master is running. Assuming ROS_MASTER_URI is 192.168.0.105
```sh
ros_ip=$(ip a s eth0 | egrep -o 'inet [0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' | cut -d' ' -f2)
ros_master_uri=192.168.0.105
export ROS_MASTER_URI=http://$ros_master_uri:11311
export ROS_IP=$ros_ip
```
## License
**Free Software, Hell Yeah!**

## Authors
- [Rahul Gupta](https://github.com/rahulelex)
