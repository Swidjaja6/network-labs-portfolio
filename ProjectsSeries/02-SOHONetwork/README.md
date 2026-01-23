# Design and Implementation of a SOHO Network Project

## Prompt

XYZ company is a fast-growing company in Eastern Australia with more than 2 million customers globally. The company deals with selling and buying of food items, which are basically operated from the headquarters. The company is intending to open a branch near the local village Bonalbo. Thus, the company requires young IT graduates to design the network for the branch. The network is intended to operate separately from the HQ network. Being a small network, the company has the following requirements during implementation;

- One router and one switch to be used (all CISCO products).
- 3 departments (Admin/IT, Finance/HR and Customer service/Reception).
- Each department is required to be in different VIANS.
- Each department is required to have a wireless network for the users.
- Host devices in the network are required to obtain IPv4 address automatically.
- Devices in all the departments are required to communicate with each other.

Assume the ISP gave out a base network of 192.168.1.0, you as the young network engineer who has been hired, design and implement a network considering the above requirements. 

## Start

Network = 192.168.1.0

One would need to have three subnets here

Subnet Mask = 255.255.255.192 or /26

## 1st Subnet

Network ID = 192.168.1.0
Valid hosts = 192.168.1.1 - 192.168.1.62
Broadcast ID = 192.168.1.63

## 2nd Subnet

Network ID = 192.168.1.64
Valid hosts = 192.168.1.65 - 192.168.1.126
Broadcast ID = 192.168.1.127

## 3rd Subnet

Network ID = 192.168.1.128
Valid hosts = 192.168.1.129 - 192.168.1.190
Broadcast ID = 192.168.1.191

## Challenges:
Up to this point in my study for the CCNA, I knew how to segment my switch for multiple vlans and configure router on a stick (ROAS) for the router. I also made the straight-through connection from the router to the switch a trunk connection. 

The challenge was to assign my IP addresses through DHCP. To do this, I had to go to global configuration mode. Then, I proceeded to do IP DHCP for each interface. After that, I had to set each device to get its IP address through DHCP

### Commands

*ip dhcp pool \[name\]*
- This command creates the dhcp pool and allows you to assign the name of it.

*network \[network-address\] \[subnet mask\]*
- This command is to assign the network IP address and the subnet mask of the dhcp pool

*default-router \[ip-address\]*
- Assigns the default-router ip address

*domain-name \[domain-name\]*
- Assigns the domain name