*This project has been created as part of the 42 cursus by tobesson*
# NetPrtactice

## Description
NetPractice is a general practical exercise designed to introduce the basics
of computer networking. The goal is to understand how TCP/IP addressing works,
including IP addresses, subnet masks, and default gateways, by configuring
small-scale simulated networks. The project provides a browser-based training
interface with 10 levels: on each level a non-functioning network diagram is
displayed, and the available configuration must be adjusted until the network
functions properly.

## Instructions
- Download the file attached to the project's page and extract it into any
  folder of your choice.
- Run the `run.sh` script to launch a local web server and open the training
  interface in your preferred web browser.
- If `run.sh` does not function properly, run
  `python3 -m http.server 49242` (any other port may be chosen) and navigate
  to `http://localhost:49242`.
- Enter your login in the training interface so your personal configuration
  is used.
- For each level, fill in the unshaded fields and click [Check again] until
  the configuration is correct, then click [Get my config] to export it.
- Export one configuration file per level (10 files in total) and place them
  at the root of your Git repository before submitting.

## Resources

### AI Usage
AI was only used to correct this README file. It was not used anywhere else.

### TCP/IP Addressing
IP adresses are used to identify devices on the internet. They are composed of 4 octets, each ranging from 0 to 255, and are usually written in dotted decimal notation (e.g., 192.168.1.42 )
TCP is a way of sending information to an adress. (Like Chronopost / UPS/ etc...)
TCP is a protocol that ensures reliable delivery of data between devices on a network. It establishes a connection between the sender and receiver, breaks the data into packets, and ensures that all packets are received and reassembled in the correct order.

#### Reserved IP Addresses
- x.x.x.255: This is the broadcast address, used to send messages to all devices on a network.
- 10.0.0.0/8: This is the private address space, used for internal networks.
- 0.0.0.0/8: This is the default route, used for local network traffic.
- 127.0.0.0/8: This is the loopback address, used for local testing.
- 172.16.0.0/12: This is the private address space, used for internal networks.
- 192.168.0.0/16: This is also the private address space, again used for internal networks.
- The first ip address in a subnet is reserved for the network address, and the last ip address in a subnet is reserved for the broadcast address.

### Subnet Masking
A mask is a way of dividing an IP address into two parts: the network part and the host part. The network part identifies the network that the device is on, while the host part identifies the specific device on that network. The subnet mask is used to determine which part of the IP address is the network part and which part is the host part.
Exmaple:
with a subnet mask of 255.255.255.0, if the host adress is 192.168.1.1, the network part is 192.168.1 and the host part is 1. This means that all devices on the same network will have the same network part (from 192.168.1.0 to 192.168.1.255), and the host part will be unique to each device (from 1 to 254).

Another way to write a subnet mask is to use / notation, which indicates the number of bits used for the network part. For example, a subnet mask of 255.255.255.0 can be written as /24.
Each time the subnet mask is increased by 1, the number of available host addresses is halved.

Common subnet masks and their corresponding / notation are:
- /0: Everything
- /8: 255.0.0.0
- /16: 255.255.0.0
- /24: 255.255.255.0
- /32: 255.255.255.255

And for netpractice some common masks are:
- /30: 255.255.255.252  >> 4 IP
- /29: 255.255.255.248  >> 8 IP
- /28: 255.255.255.240  >> 16 IP
- /27: 255.255.255.224  >> 32 IP
- /26: 255.255.255.192  >> 64 IP
- /25: 255.255.255.128  >> 128 IP
- /24: 255.255.255.0    >> 256 IP

### Default Gateway
The default gateway is the IP address of the device that routes traffic from the local network to other networks, such as the internet.
We can use default or 0.0.0.0/0 to indicate the default route. (Easiest way to go to the internet)

### Router / Switch
A router is a device that forwards data packets between different networks. A switch is a device that connects devices within the same network.

Only the router separate networks, the switch only duplicate packets to all device of the network.
A switch is used when having 

### OSI Layers
The OSI (Open Systems Interconnection) layers are a system for understanding how the systems works.
It consist of 7 layers, each independent of the others for a better matainablity. Each layer has a specific function and communicates with the layers above and below it.

The layers consist of:
1. Physical Layer: This layer is responsible for the physical connection between devices. (radio signals, cables, etc...)
2. Data Link Layer: This layer is responsible for the reliable transfer of data between devices on the same network. (Ethernet, Wi-Fi, etc...)
3. Network Layer: This layer is responsible for routing data packets between different networks. (IP, ICMP, etc...)
4. Transport Layer: This layer is responsible for ensuring the reliable delivery of data between devices on a network. (TCP, UDP, etc...)
5. Session Layer: This layer is responsible for establishing, maintaining, and terminating sessions between devices on a network. (SSL, TLS, etc...)
6. Presentation Layer: This layer is responsible for translating data between different formats and ensuring that data is presented in a way that is understandable to the receiving device. (JPEG, MPEG, etc...)
7. Application Layer: This layer is responsible for providing services to the user. (HTTP, FTP, SMTP, etc...)

The most interesting are the 2,3 and 7. For netpractice we only need to understand the 3rd layer

### 