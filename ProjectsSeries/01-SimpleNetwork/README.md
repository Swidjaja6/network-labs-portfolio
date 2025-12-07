# Design and Implementation of a Simple Networking Project

## Prompt

Design a network in Cisco Packet Tracer to connects ACCOUNTS and DELIVERY departments through the following:

- Each department should contain at least two PCs.
- Appropriate number of switches and routers should be used in the network.
- Using the given network 192.168.40.0, all interfaces sould be configured with correct IP addresses, subnet mask and gateways.
- All devices in the network should be connected using appropriate cables.
- Test communication between devices in both ACCOUNTS and DELIVERY departments.

## Start

Network = 192.168.40.0

One would need to have two subnets here

Subnet Mask = 255.255.255.128 or /25

## 1st Subnet

Network ID = 192.168.40.0
Valid hosts = 192.168.40.1 - 192.168.40.126
Broadcast ID = 192.168.40.127

## 2nd Subnet

Network ID = 192.168.40.128
Valid hosts = 192.168.40.129 - 192.168.40.254
Broadcast ID = 192.168.40.255

## Challenges:
Connecting a laptop with a copper straight-through wire is requires an Ethernet NIC. In Cisco Packet Tracer, the PT-LAPTOP-NM-1CFE is the default NIC on the laptops. To connect to the switch wirelessly, one needs to switch out the NIC and replace it with a wireless module like the WPC300N. However, this does not work on a regular ISR4331 router. 