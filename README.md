# 📘 Campus Network Design – README

## 📌 Project Overview

This project demonstrates the design and implementation of a **secure campus network** using Cisco networking devices in **Cisco Packet Tracer**. The topology integrates **routing, switching, firewall security, IPv4/IPv6 addressing, dynamic routing, DHCP, ACLs, and IoT connectivity** following enterprise best practices.

The network is divided into **Office, Factory, DMZ, and IoT zones**, protected by a **Cisco ASA 5506-X firewall**, with **OSPF** used for dynamic routing and **VLAN + Spanning Tree** for Layer 2 redundancy.

---

## 🧾 Tasks Implemented

* ✅ Campus network design
* ✅ VLAN creation and Spanning Tree Protocol (PVST)
* ✅ Network security using Cisco ASA firewall
* ✅ IPv4 and IPv6 configuration
* ✅ OSPF (Open Shortest Path First) routing
* ✅ DHCP configuration (IPv4 & IPv6)
* ✅ ACLs (Access Control Lists)
* ✅ IoT device connectivity with IPv6

---

## 🧩 Network Components

### 🔧 Devices Used

* **Firewall**: Cisco ASA 5506-X (1)
* **Routers**: Cisco ISR4331 (4)
* **Switches**:

  * Multilayer Switch: Cisco 3560-24PS (2)
  * Layer 2 Switch: Cisco 2960-24TT (5)
* **Servers**: Server-PT
* **End Devices**: PC-PT (6), Smartphones
* **Wireless & IoT**:

  * Home Gateway (DLC100)
  * Access Point-PT
  * MCU (Micro Controller Unit)
  * IoT Devices (Sensors, RFID, etc.)
  * Cell Tower

---

## 🌐 Network Segments

| Zone       | Network            | Purpose               |
| ---------- | ------------------ | --------------------- |
| Office     | 10.1.1.0/24        | Corporate users       |
| Factory    | 20.1.1.0/24        | Industrial users      |
| DMZ        | 30.1.1.0/24        | Public-facing servers |
| Inside     | 192.168.100.0/24   | Trusted internal zone |
| Outside    | 192.168.200.0/24   | External / ISP side   |
| DMZ (ASA)  | 192.168.150.0/24   | Semi-trusted zone     |
| IoT (IPv6) | 2001:DB8:10:1::/64 | IoT devices           |

---

## 🔀 Routing Protocol

* **OSPF Area 0** implemented on all routers and ASA
* Provides dynamic route exchange between Office, Factory, DMZ, and Firewall networks

---

## 📡 DHCP Configuration

### IPv4 DHCP

* Router 0 → Office network (10.1.1.0/24)
* Router 1 → Factory network (20.1.1.0/24)
* Router 2 → DMZ internal network (30.1.1.0/24)
* ASA provides DHCP for:

  * Inside (192.168.100.0/24)
  * Outside (192.168.200.0/24)
  * DMZ (192.168.150.0/24)

### IPv6 DHCP

* Router 3 provides **stateful IPv6 DHCP** for IoT devices
* Prefix: `2001:DB8:10:1::/64`

---

## 🔐 Firewall (Cisco ASA 5506-X)

### Security Zones

* **Inside** – Security level 100
* **DMZ** – Security level 50
* **Outside** – Security level 0

### NAT

* Dynamic PAT for Inside → Outside
* DMZ servers protected via ACLs

### ACL Policy Summary

| Traffic Flow     | Status            |
| ---------------- | ----------------- |
| Inside → Outside | ✅ Allowed         |
| Inside → DMZ     | ✅ Allowed         |
| Outside → Inside | ❌ Blocked         |
| Outside → DMZ    | ✅ Only HTTP/HTTPS |
| DMZ → Inside     | ❌ Blocked         |

ICMP is selectively permitted for testing and monitoring.

---

## 🔗 VLAN & Spanning Tree

* VLANs configured on access switches for segmentation
* Trunk links between switches and multilayer switches
* **PVST (Per-VLAN Spanning Tree)** enabled
* Multilayer switch acts as **STP Root Bridge**

---

## 🌐 IoT & IPv6 Integration

* IoT devices connected through Home Gateway and MCU
* IPv6 addressing with DHCPv6
* Centralized IPv6 gateway and DNS configuration

---

## 🧪 Verification & Testing

* `show ip route` / `show ipv6 route`
* `show ip ospf neighbor`
* `show spanning-tree`
* Ping & ICMP tests across zones
* DHCP address assignment verification

---

## 🎯 Learning Outcomes

* Practical understanding of enterprise campus design
* Hands-on firewall security with ASA
* Integration of IPv4, IPv6, and IoT networks
* Real-world routing, switching, and security concepts

---

## 📎 Tools Used

* Cisco Packet Tracer
* Cisco IOS & ASA CLI

---
