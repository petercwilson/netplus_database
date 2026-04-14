# Labs – Scenario-Based Configurations

This directory contains hands-on lab scenarios aligned to CompTIA Network+ N10-009 objectives. Labs use **Cisco Packet Tracer** and/or **Wireshark** unless otherwise noted.

---

## 🧰 Prerequisites

| Tool | Download | Cost |
|------|----------|------|
| Cisco Packet Tracer | [netacad.com](https://www.netacad.com/courses/packet-tracer) | Free (requires Cisco NetAcad account) |
| Wireshark | [wireshark.org](https://www.wireshark.org/) | Free |
| GNS3 (optional) | [gns3.com](https://www.gns3.com/) | Free (requires router images) |

---

## 📋 Lab Index

### Domain 1 – Networking Fundamentals

| Lab | Tool | Objective |
|-----|------|-----------|
| [Lab 1.1 – OSI Layer Analysis with Wireshark](./Lab-1.1-OSI-Wireshark.md) | Wireshark | Identify protocols at each OSI layer in a packet capture |
| [Lab 1.2 – IPv4 Subnetting Practice](./Lab-1.2-IPv4-Subnetting.md) | Paper / Calculator | Practice CIDR subnetting with real-world scenarios |
| [Lab 1.3 – IPv6 Address Configuration](./Lab-1.3-IPv6-Config.md) | Packet Tracer | Configure dual-stack IPv4/IPv6 on a router |

### Domain 2 – Network Implementations

| Lab | Tool | Objective |
|-----|------|-----------|
| [Lab 2.1 – Static and Dynamic Routing (OSPF)](./Lab-2.1-OSPF-Routing.md) | Packet Tracer | Configure OSPF between three routers |
| [Lab 2.2 – VLAN Configuration and Trunking](./Lab-2.2-VLAN-Trunk.md) | Packet Tracer | Create VLANs, assign ports, configure 802.1Q trunk |
| [Lab 2.3 – Wireless Security Modes](./Lab-2.3-Wireless-Security.md) | Packet Tracer | Configure WPA2-PSK and WPA2-Enterprise on a WAP |

### Domain 3 – Network Operations

| Lab | Tool | Objective |
|-----|------|-----------|
| [Lab 3.1 – DHCP Server Configuration](./Lab-3.1-DHCP.md) | Packet Tracer | Configure a DHCP scope, exclusions, and reservations |
| [Lab 3.2 – DNS Record Analysis](./Lab-3.2-DNS.md) | Wireshark / nslookup | Capture and analyze DNS queries and responses |
| [Lab 3.3 – SNMP Monitoring Setup](./Lab-3.3-SNMP.md) | Packet Tracer | Configure SNMPv3 on a router and poll from a manager |

### Domain 4 – Network Security

| Lab | Tool | Objective |
|-----|------|-----------|
| [Lab 4.1 – ACL Configuration](./Lab-4.1-ACL.md) | Packet Tracer | Apply standard and extended ACLs to filter traffic |
| [Lab 4.2 – Port Security on a Switch](./Lab-4.2-Port-Security.md) | Packet Tracer | Enable sticky MAC, set violation modes |
| [Lab 4.3 – Wireshark ARP Analysis](./Lab-4.3-ARP-Analysis.md) | Wireshark | Observe ARP requests/replies; detect ARP anomalies |
| [Lab 4.4 – Site-to-Site VPN Configuration](./Lab-4.4-IPsec-VPN.md) | Packet Tracer | Configure IPsec site-to-site VPN between two routers |

### Domain 5 – Network Troubleshooting

| Lab | Tool | Objective |
|-----|------|-----------|
| [Lab 5.1 – Troubleshooting Connectivity (7 Steps)](./Lab-5.1-Troubleshooting-Methodology.md) | Packet Tracer | Apply the CompTIA 7-step process to a broken network |
| [Lab 5.2 – Wireshark Traffic Capture](./Lab-5.2-Wireshark-Capture.md) | Wireshark | Capture traffic, apply filters, identify anomalies |
| [Lab 5.3 – CLI Diagnostic Tools](./Lab-5.3-CLI-Diagnostics.md) | Terminal | Use ping, traceroute, netstat, nslookup, arp |

---

## 🏆 Challenge Scenarios

These end-to-end scenarios combine skills from multiple domains:

| Scenario | Description | Domains Covered |
|----------|-------------|----------------|
| [Scenario A – Building a Small Office Network](./Scenario-A-Small-Office.md) | Design and configure a complete small office network from scratch | 1, 2, 3 |
| [Scenario B – Security Hardening Audit](./Scenario-B-Security-Audit.md) | Audit and harden an existing network against common attacks | 4 |
| [Scenario C – Incident Response Simulation](./Scenario-C-Incident-Response.md) | Respond to a simulated network outage using the 7-step method | 5 |

---

## 📝 Lab Submission Template

When completing a lab, document your work using this structure:

```
Lab: [Lab name and number]
Date: [Date completed]
Objective: [What you set out to do]
Topology: [Brief description or screenshot reference]
Steps Taken: [Step-by-step what you did]
Results: [What happened; screenshots if available]
Lessons Learned: [What you learned or what surprised you]
```
