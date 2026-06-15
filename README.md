
# CCNA Networking Project – VLAN Segmentation with Router-on-a-Stick

## 1. Project Overview

This project demonstrates core **CCNA networking concepts** using **Cisco Packet Tracer**. The network is logically segmented using **VLANs** for different departments. **Inter-VLAN communication** is achieved using **Router-on-a-Stick (ROAS)**. **DHCP** is implemented for automatic IP assignment, an **Access Control List (ACL)** secures the server, and **port security** is used to prevent unauthorized devices.

---

## 2. Network Topology

### Devices Used

* **1 Router**
* **2 Switches**
* **Multiple PCs**
* **1 Server**

### Connections

* Router **G0/0 → Switch0 Fa0/24** *(Trunk)*
* Switch0 **Fa0/23 → Switch1 Fa0/23** *(Trunk)*
* PCs connected to **access ports**
* Server connected to **Switch0 (VLAN 47)**

---

## 3. VLAN Design

| Department | VLAN ID | Network        |
| ---------- | ------- | -------------- |
| HR         | 10      | 172.16.10.0/24 |
| IT         | 20      | 172.16.20.0/24 |
| Sales      | 30      | 172.16.30.0/24 |
| Management | 40      | 172.16.40.0/24 |
| Server     | 47      | 172.16.47.0/24 |

---

## 4. Key Features Implemented

* VLAN segmentation for departments
* 802.1Q trunking between switches and router
* Router-on-a-Stick for inter-VLAN routing
* DHCP for automatic IP addressing
* ACL to restrict server access
* Port security to prevent unauthorized devices

---

## 5. IP Addressing Plan

| VLAN | Department | Network          | Assignment |
| ---- | ---------- | ---------------- | ---------- |
| 10   | HR         | `172.16.10.0/24` | DHCP       |
| 20   | IT         | `172.16.20.0/24` | DHCP       |
| 30   | Sales      | `172.16.30.0/24` | DHCP       |
| 40   | Management | `172.16.40.0/24` | DHCP       |
| 47   | Server     | `172.16.47.0/24` | Static     |

> Default gateways are configured on router subinterfaces.

---

## 6. Sample Configuration

### Router Configuration

```bash
interface g0/0.10
 encapsulation dot1Q 10
 ip address 172.16.10.1 255.255.255.0

interface g0/0.47
 encapsulation dot1Q 47
 ip address 172.16.47.1 255.255.255.0
```

### ACL Configuration

```bash
access-list 100 permit ip 172.16.10.0 0.0.0.255 host 172.16.47.2
access-list 100 deny ip any host 172.16.47.2
access-list 100 permit ip any any
```

---

## 7. Security Implementation

### ACL Policy

* HR VLAN is allowed to access the server
* All other VLANs are denied server access

### Additional Security

* Switch port security enabled
* MAC address limiting on access ports
* Unauthorized devices automatically blocked

---

## Technologies Used

* Cisco Packet Tracer
* VLANs & Trunking
* Router-on-a-Stick
* DHCP
* Access Control Lists (ACL)
* Port Security

---

## Project Outcome

This setup improves **network performance, security, and department isolation** while ensuring **controlled server access for sensitive HR resources**.

