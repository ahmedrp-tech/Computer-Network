# 🖧 University Network Design Project — COM204

## 📘 Course Information
- **Course Title:** Computer Networks  
- **Instructor:** Prof. Dr. Mahmoud Elmesalawy  

---

## 👨‍🎓 Student Details
- **Student Name:** Ahmed Sameh Ibrahim   
- **Student ID:** 932230013 

---

## 🧠 Project Description
This project focuses on planning and implementing a **scalable and secure computer network infrastructure** for **Helwan National University** as part of a course assignment.

Phase 1 of the design connects **four major university buildings**:

1. Administration Building  
2. Faculty of Engineering  
3. Faculty of Computer Science & Information Technology  
4. Faculty of Medicine  

The design ensures that each building can communicate reliably while maintaining structured management of:

- IP addressing and subnetting
- VLAN segmentation
- Routing & inter-building communication
- Secure remote access for administrators

---

## 🏗️ Network Architecture
The topology was developed in **Cisco Packet Tracer** and consists of:

- **4 Routers** (one router per building)
- **4 Cisco 2960 Switches**
- **24 Workstations** (representing university departments such as IT, HR, Student Affairs)
- **VLANs** for department-based network isolation
- **Remote Management** enabled via **Telnet**
- **Routing** implemented through a hybrid of **RIP** and **static routes**

---

## 🧩 Key Network Features

### ✔ Subnetting and IP Planning
- Utilized **VLSM (Variable Length Subnet Masking)** to reduce IP waste
- Each department assigned to its own subnet for better management

### ✔ VLAN Implementation
Department | VLAN | Purpose
---|---|---
Human Resources | 10 | Confidential staff network  
IT Department | 20 | Technical operations  
Student Affairs | 30 | Student services and records  

### ✔ Routing Design
- Dynamic routing using **RIPv2**
- Static routes used when applicable
- Inter-VLAN routing supported to allow controlled communication

---

## 🧮 Example Subnet Allocation

Building / Department | VLAN ID | Subnet | Mask | Host Range | Broadcast
---|---|---|---|---|---
Admin — HR | 10 | 10.0.0.0/26 | 255.255.255.192 | 10.0.0.1 – 10.0.0.62 | 10.0.0.63  
Engineering — IT | 20 | 10.0.0.64/26 | 255.255.255.192 | 10.0.0.65 – 10.0.0.126 | 10.0.0.127  
CSIT — Student Affairs | 30 | 10.0.0.128/26 | 255.255.255.192 | 10.0.0.129 – 10.0.0.190 | 10.0.0.191  

> Note: These values represent an example allocation; the final Packet Tracer file includes the full addressing plan.

---

## 🔧 Sample Router Configuration Snippet

`bash
Router> enable
Router# configure terminal
Router(config)# hostname Amr-CS-Router
Router(config)# enable password 123

Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.62 255.255.255.192
Router(config-if)# no shutdown

Router(config)# interface g0/4
Router(config-if)# ip address 12.0.0.2 255.255.255.0
Router(config-if)# no shutdown
🧪 Network Verification
Several tests were executed to validate network operations:

✔ Building-to-building communication via ICMP (Ping)
✔ Inter-VLAN connectivity through routing
✔ Telnet administrator access on routers and switches
✔ DHCP functioning across all departments
✔ Routing table inspection using show ip route

🚧 Issues Encountered & Fixes
Issue	Resolution
Incorrect VLAN assignment	Reconfigured port-to-VLAN mappings
Route table inconsistencies	Reviewed output of show ip route, corrected RIP settings
IP conflicts & addressing errors	Reorganized VLSM and DHCP pools
Telnet access failure	Checked line configurations & access control

📌 Final Result
By the end of Phase 1, the designed network successfully delivered:

🔗 Full inter-building connectivity

🧩 Logical traffic segmentation via VLANs

📊 Efficient IP usage through VLSM

🔐 Secure administrative access using Telnet

📡 Dynamic routing for scalable expansion

The network is ready for future stages to integrate additional faculties across the university.

📎 Included Project Files
Project.pkt → Full Packet Tracer topology & configurations

README.md → Project summary and technical highlights
