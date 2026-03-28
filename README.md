# CCNA Networking Project – VLAN Segmentation with Router-on-a-Stick

## 📌 Project Overview
This project demonstrates core CCNA networking concepts using Cisco Packet Tracer. The network is logically segmented using VLANs for different departments.

Key implementations:
- Inter-VLAN communication using Router-on-a-Stick
- DHCP for automatic IP assignment
- ACL for security
- Port security to prevent unauthorized access

---

## 🖥️ Network Topology

### Devices Used
- 1 Router
- 2 Switches
- Multiple PCs
- 1 Server

### Connections
- Router G0/0 → Switch0 Fa0/24 (Trunk)
- Switch0 Fa0/23 ↔ Switch1 Fa0/23 (Trunk)
- PCs connected to access ports
- Server connected to Switch0 (VLAN 47)

---

## 🌐 VLAN Design

| Department  | VLAN ID | Network            |
|------------|--------|------------------|
| HR         | 10     | 172.16.10.0/24   |
| IT         | 20     | 172.16.20.0/24   |
| Sales      | 30     | 172.16.30.0/24   |
| Management | 40     | 172.16.40.0/24   |
| Server     | 47     | 172.16.47.0/24   |

---

## ⚙️ Key Features

- VLAN segmentation
- 802.1Q trunking
- Router-on-a-Stick
- DHCP configuration
- ACL security rules
- Port security (Sticky MAC)

---

## 📡 IP Addressing Plan

- HR VLAN: 172.16.10.0/24 (DHCP)
- IT VLAN: 172.16.20.0/24 (DHCP)
- Sales VLAN: 172.16.30.0/24 (DHCP)
- Management VLAN: 172.16.40.0/24 (DHCP)
- Server VLAN: 172.16.47.0/24 (Static)

Default gateways are configured on router subinterfaces.

---

## 🧠 Configuration

### Router Configuration
```bash
interface g0/0.10
 encapsulation dot1Q 10
 ip address 172.16.10.1 255.255.255.0

interface g0/0.47
 encapsulation dot1Q 47
 ip address 172.16.47.1 255.255.255.0