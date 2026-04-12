# Design and Implementation of an Hotel System

## Prompt

As a part of your end year networking project, you are required to design and implement Vic Modern Hotel network. The hotel has three floors; in the first floor there three departments (Reception, store and Logistics), in the second floor there are three departments (Finance, HR and Sales/Marketing), while the third floor hosts the IT and Admin. Therefore, the following are part of the considerations during the design and implementation

- There should be three routers connecting each floor (all placed in the server room in IT department).
- All routers should be connected to each other using serial DCE cable.
- The network between the routers should be 10.10.10.0/30,10.10.10.4/30 and 10.10.10.8/30.
- Each floor is expected to have one switch (placed in the respective floor).
- Each floor is expected to have WIFI networks connected to laptops and phones.
- Each department is expected to have a printer.
- Each department is expected to be in different VLAN with the following details;
  - 1st Floor;
    - Reception- VLAN 80, Network of 192.168.8.0/24
    - Store- VLAN 70, Network of 192.168.7.0/24
    - Logistics- VLAN 60, Network of 192.168.6.0/24
  - 2nd Floor;
    - Finance- VLAN 50, Network of 192.168.5.0/24
    - HR- VLAN 40, Network of 192.168.4.0/24
    - Sales- VLAN 30, Network of 192.168.3.0/24
  - 3rd Floor;
    - Admin- VLAN 20, Network of 192.168.2.0/24
    - IT- VLAN 10, Network of 192.168.1.0/24

- Use OSPF as the routing protocol to advertise routes.
- All devices in the network are expected to obtain IP address dynamically with their respective router configured as the DHCP server.
- All the devices in the network are expected to communicate with each other.
- Configure SSH in all the routers for remote login.
- In IT department, add PC called Test-PC to port fa0/1 and use it to test remote login.
- Configure port security to IT-dept switch to allow only Test-PC to access port fa0/1 (use sticky method to obtain mac-address with violation mode of shutdown.)

## Start

Networks:
- 10.10.10.x
- 192.168.x.0

One would need to have three subnets here

Subnet Masks
- 255.255.255.252 for the Server room
- 255.255.255.0 for departments

## Floor 1 Networks

Reception
- Vlan 80
- Network ID = 192.168.8.0
- Valid hosts = 192.168.8.1 - 192.168.8.254
- Broadcast ID = 192.168.8.255

Store
- Vlan 70
- Network ID = 192.168.7.0
- Valid hosts = 192.168.7.1 - 192.168.7.254
- Broadcast ID = 192.168.7.255

Logistics
- Vlan 60
- Network ID = 192.168.6.0
- Valid hosts = 192.168.6.1 - 192.168.6.254
- Broadcast ID = 192.168.6.255
## Floor 2 Networks

Logistics
- Vlan 50
- Network ID = 192.168.5.0
- Valid hosts = 192.168.5.1 - 192.168.5.254
- Broadcast ID = 192.168.5.255

Logistics
- Vlan 40
- Network ID = 192.168.4.0
- Valid hosts = 192.168.4.1 - 192.168.4.254
- Broadcast ID = 192.168.4.255

Logistics
- Vlan 30
- Network ID = 192.168.3.0
- Valid hosts = 192.168.3.1 - 192.168.3.254
- Broadcast ID = 192.168.3.255

## Floor 3 Networks

Logistics
- Vlan 20
- Network ID = 192.168.2.0
- Valid hosts = 192.168.2.1 - 192.168.2.254
- Broadcast ID = 192.168.2.255

Logistics
- Vlan 10
- Network ID = 192.168.1.0
- Valid hosts = 192.168.1.1 - 192.168.1.254
- Broadcast ID = 192.168.1.255

## Challenges:
I waited until I finished my learning to do this project. I had to apply many concepts that I had learned throughout the course to finish it. The previous project I did required me to make VLANs, but this time there were more and I had to do inter-vlan routing. I had to have IP addresses assigned to devices again by DHCP, and I had to create a DHCP service for each subinterface in my Router on a Stick (ROAS) implementation. 

One of the biggest challenges was implementing Open Shortest Path First (OSPF) dynamic routing. The third floor devices were not initially communicating with the rest of the devices in the other floors. I found out that I set the wildcard mask wrong on implementation. Once I fixed it, the floor devices were able to communicate with the 3rd floor and vice versa. 

## Concepts Applied
- Inter-VLAN routing (ROAS)
- SSH
- Port-Security
- WLANs
- OSPF Routing