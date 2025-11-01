# 🌐 Packet Tracer Network Lab - A Comprehensive Corporate Network
=================================================

## 📌 Description
-----------
  This project simulates an advanced corporate network environment using Cisco Packet Tracer. 
  It demonstrates the design and implementation of a secure and scalable network for a main office and a branch office, 
  showcasing real-world concepts such as VLANs, dynamic routing (OSPF), network address translation (NAT), IPv6, and access control lists (ACLs).

## 🎯 Objectives
----------
- Configure VLANs to segment network traffic and enhance security.

- Implement dynamic routing using OSPF for both IPv4 and IPv6 to ensure network 
  scalability and efficiency.
  
- Set up NAT to allow internal devices to access an external network (Internet).

- Establish a secure site-to-site connection using a GRE Tunnel.

- Integrate IPv6 to prepare the network for modern internet protocols.

- Apply ACLs to control and restrict traffic between different network segments.

- Configure Quality of Service (QoS) to prioritize mission-critical traffic.

## 🛠 Equipment Used
--------------
- 2x Cisco 2911 Router
- 2x Cisco 2960 Switch
- 3x PC
- 1x Cloud-PT
- Cisco Packet Tracer 8.2.2.0400

## Key Concepts
------------
- VLANs (Virtual Local Area Networks): The network is logically segmented into three distinct VLANs to isolate traffic and reduce broadcast domains. 
  VLAN 10 and VLAN 20 are in the main office, while VLAN 30 is in the branch office.

- Router-on-a-Stick: On both routers, a single physical interface is configured with logical sub-interfaces to route traffic between the VLANs, 
  optimizing resource usage.

- NAT (Network Address Translation): A form of NAT called Port Address Translation (PAT) is configured on Router1 to translate private IPv4 addresses into a single public address, 
  enabling all internal devices to communicate with the Cloud.

- IPv6: The network is configured with SLAAC (Stateless Address Autoconfiguration), allowing devices to automatically generate their own unique IPv6 addresses, 
  simplifying network management.
  
- Dynamic Routing (OSPF): Instead of static routes, OSPF is configured for both IPv4 and IPv6 (OSPFv2 and OSPFv3) to allow the routers to automatically discover and share routing information, 
  ensuring the network is scalable and resilient to topology changes.
  
- GRE Tunnel: A secure, site-to-site tunnel is established between the main office and the branch office.

- ACLs (Access Control Lists): A security rule is implemented on Router1 to explicitly deny communication from VLAN 10 to VLAN 20, while permitting all other traffic.

- QoS: Traffic from a specific VLAN is prioritized to guarantee a certain level of performance.

## 🔧 Configuration Summary
---------------------
- Router1: Manages inter-VLAN routing, provides DHCP and SLAAC services for its subnets, and handles NAT to the Cloud. It uses OSPF to dynamically route traffic to Router2.
- Router2: Manages the branch office network and uses OSPF to dynamically route traffic to Router1.
- Switch1 & Switch2: Segment their respective networks, assigning PCs to VLANs and using trunk ports to communicate with the routers.
- Cloud-PT: Acts as a WAN (Wide Area Network) simulator, serving as the gateway to the Internet.


# Project Evolution: From Static to Dynamic
---------------------
 This section details the key changes and fixes I made during the project. It shows how the network evolved from a basic static setup to a more advanced, dynamic, and realistic topology.

- Router Model Change: I initially used Cisco 4331 routers. However, I found that these models have a limited number of physical ports, which was insufficient for my design. To fix this, I replaced them with        Cisco 2911 routers, which provided the necessary ports for all connections (LAN, WAN, and Cloud).

- Cloud-PT Configuration: The Cloud-PT device in Packet Tracer 8.2.2.0400 is a special WAN emulator. I initially had some confusion because it doesn't allow a direct IP address configuration on
  its interfaces. I resolved this by assigning the public IP address (209.165.200.1) directly to the Router1 interface connected to the cloud, treating the cloud as a transparent bridge.

- Routing Protocol: The initial configuration used static routes for both IPv4 and IPv6. While functional, I realized this approach is not scalable. I replaced all static routes with the OSPF protocol,
  which allows the routers to automatically learn about new networks, simplifying future expansion and improving network resiliency.

- IPv6 Addressing: I noticed that the PCs were receiving IPv6 addresses with a unique host portion, which seemed unexpected at first. I confirmed that this is the correct behavior of SLAAC, where each host          automatically generates its unique address based on its MAC address and the network prefix from the router.

- ACL Behavior: The ping test from PC1 to PC2 resulted in a "Destination host unreachable" message instead of "Request timed out." I learned that this is a valid and correct response from the router,
  indicating that the ACL is working by explicitly denying the traffic and sending an ICMP message back to the source.


## 📷 Screenshots
-----------
- Network Diagram: diagram.png
- IPv6 Ping Test: screenshots/ping_test_pc.png

## 🚀 How to Run
----------
1. Open corporate_network_project.pkt in Cisco Packet Tracer.
2. Start the simulation.
3. Verify network connectivity by pinging devices from different VLANs.

## Summary
-------
This project successfully demonstrates how to build a scalable, organized, and secure corporate network. 
By integrating dynamic routing, IPv6, NAT, and ACLs, it highlights key principles of modern network infrastructure design and configuration.

=================================================
# Author: Serhii Gorin 
# Date: 23.08.2025

---
## ⚠️ Disclaimer
This is an educational project for portfolio purposes. Cisco Packet Tracer and all associated logos are the property of Cisco Systems, Inc.
