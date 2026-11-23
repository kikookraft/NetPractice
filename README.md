*This project has been created as part of the 42 cursus by tobesson*
# NetPrtactice

## Description

NetPractice is a practical networking exercise that introduces the basics of
TCP/IP addressing. The goal is to configure small simulated networks by setting
IP addresses, subnet masks, routers, and default gateways so that every device
can communicate according to the exercise objectives.


## Instructions

- Download the project archive and extract it into a directory of your choice.
- Run `./run.sh` from the project directory to start a local web server and open
  the training interface.
- If `run.sh` does not work, start a server manually with
  `python3 -m http.server 49242` and open `http://localhost:49242`.
- Enter your 42 login in the interface. The `Evaluation` tab can be used to
  generate a random configuration for practice or evaluation.
- Modify the unshaded fields in the network diagram.
- Use `Check again` to verify the configuration and read the logs if a check fails.
- Once a level is valid, use `Get my config` to export its configuration.
- Submit the 10 exported files, `level1.json` through `level10.json`, at the
  root of the Git repository. Do not rely on the state of the interface for the
  defense; keep the exported files in the repository.

## Resources

The concepts studied in this project include:

- **TCP/IP addressing:** IPv4 addresses are written as four decimal octets and
  identify devices participating in an IP network. TCP is a transport protocol
  that provides reliable, ordered, bidirectional byte-stream communication.
- **Subnet masks:** A subnet mask separates the network and host portions of an
  IPv4 address. For example, `255.255.255.0` is `/24`: the first 24 bits identify
  the network and the final 8 bits identify hosts.
- **Network and broadcast addresses:** In a conventional IPv4 subnet, the first
  address is reserved for the network and the final address is reserved for
  broadcast. Therefore, neither address is usually assigned to a normal host.
  Address `x.x.x.255` is a broadcast address only in a `/24` (or another subnet
  aligned with it), not in every possible subnet.
- **Default gateways:** A gateway is the address of a router used by a host to
  send traffic outside its local subnet. The default route is `0.0.0.0/0`.
- **Routers and switches:** A switch connects devices in the same local network.
  A router forwards packets between different networks and can use routing tables
  and gateway settings to choose the next hop.
- **OSI model:** The Physical, Data Link, Network, Transport, Session,
  Presentation, and Application layers separate network communication into
  distinct functions. NetPractice focuses mainly on the Network layer and IPv4,
  while TCP belongs to the Transport layer.

Useful classic references:

- [RFC 791 - Internet Protocol](https://www.rfc-editor.org/rfc/rfc791)
- [RFC 4632 - Classless Inter-domain Routing](https://www.rfc-editor.org/rfc/rfc4632)
- [Cisco: IP Addressing and Subnetting](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html)
- [MDN: An overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
- [IANA: Special-Purpose IP Address Registries](https://www.iana.org/assignments/iana-ipv4-special-registry/iana-ipv4-special-registry.xhtml)

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

#### Common Subnet Masks

| CIDR | Subnet mask | Total addresses |
|---|---|---:|
| `/30` | `255.255.255.252` | 4 |
| `/29` | `255.255.255.248` | 8 |
| `/28` | `255.255.255.240` | 16 |
| `/27` | `255.255.255.224` | 32 |
| `/26` | `255.255.255.192` | 64 |
| `/25` | `255.255.255.128` | 128 |
| `/24` | `255.255.255.0` | 256 |

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