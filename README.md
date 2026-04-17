# 📡 CompTIA Network+ N10-009 Study Repository

A structured, comprehensive resource for preparing for the **CompTIA Network+ N10-009** certification exam. This repository is organized around the five official exam domains and includes labs, cheat sheets, and study guides.

---

## 📋 Domain Checklist

| # | Domain | Weight | Status |
|---|--------|--------|--------|
| 1 | [Networking Fundamentals](./Domain-1-Networking-Fundamentals/README.md) | 23% | ☐ Not Started |
| 2 | [Network Implementations](./Domain-2-Network-Implementations/README.md) | 20% | ☐ Not Started |
| 3 | [Network Operations](./Domain-3-Network-Operations/README.md) | 17% | ☐ Not Started |
| 4 | [Network Security](./Domain-4-Network-Security/README.md) | 20% | ☐ Not Started |
| 5 | [Network Troubleshooting](./Domain-5-Network-Troubleshooting/README.md) | 20% | ☐ Not Started |

> **Tip:** Update the Status column as you complete each domain. Change `☐ Not Started` → `🔄 In Progress` → `✅ Complete`.

---

## 📁 Repository Structure

```
netplus_database/
├── Domain-1-Networking-Fundamentals/   # OSI & TCP/IP, IPv4/IPv6, Network Topologies
├── Domain-2-Network-Implementations/   # Routing, Switching, Wireless
├── Domain-3-Network-Operations/        # Monitoring, Documentation, BC/DR
├── Domain-4-Network-Security/          # Hardening, Attacks, Zero Trust
├── Domain-5-Network-Troubleshooting/   # Methodology & Tools
├── Labs/                               # Scenario-based labs (Packet Tracer, Wireshark)
└── Resources/                          # Cheat sheets: ports, subnetting, CLI commands
```

---

## 🗓️ Daily Study Routine

Use this routine as a baseline and adapt it to your schedule. Aim for **60–90 minutes per day**.

| Time Block | Activity |
|------------|----------|
| **0–10 min** | Review flashcards or notes from the previous session |
| **10–40 min** | Read & annotate the current domain's README or sub-topic notes |
| **40–60 min** | Work through a lab scenario in `/Labs` (Packet Tracer or Wireshark) |
| **60–75 min** | Answer 10–15 practice questions (use Professor Messer, Jason Dion, etc.) |
| **75–90 min** | Update your domain checklist, write a short summary, review weak areas |

### 📅 Suggested Weekly Domain Schedule

| Week | Focus |
|------|-------|
| Week 1 | Domain 1 – Networking Fundamentals |
| Week 2 | Domain 2 – Network Implementations |
| Week 3 | Domain 3 – Network Operations |
| Week 4 | Domain 4 – Network Security |
| Week 5 | Domain 5 – Network Troubleshooting |
| Week 6 | Full review, timed practice exams |

---

## 🃏 Flashcards

### Common Network Ports

| Port | Protocol | Service | Description |
|------|----------|---------|-------------|
| 20 | TCP | FTP-DATA | File Transfer Protocol – data channel |
| 21 | TCP | FTP | File Transfer Protocol – control channel |
| 22 | TCP | SSH / SFTP / SCP | Secure Shell; also used by SFTP and SCP |
| 23 | TCP | Telnet | Unencrypted remote terminal (legacy) |
| 25 | TCP | SMTP | Simple Mail Transfer Protocol – sending email |
| 53 | TCP/UDP | DNS | Domain Name System – name resolution |
| 67 | UDP | DHCP (Server) | Dynamic Host Configuration Protocol – server |
| 68 | UDP | DHCP (Client) | Dynamic Host Configuration Protocol – client |
| 69 | UDP | TFTP | Trivial File Transfer Protocol |
| 80 | TCP | HTTP | Hypertext Transfer Protocol – unencrypted web |
| 110 | TCP | POP3 | Post Office Protocol v3 – email retrieval |
| 119 | TCP | NNTP | Network News Transfer Protocol |
| 123 | UDP | NTP | Network Time Protocol |
| 143 | TCP | IMAP | Internet Message Access Protocol |
| 161 | UDP | SNMP | Simple Network Management Protocol – queries |
| 162 | UDP | SNMP Trap | SNMP – trap/notifications |
| 389 | TCP/UDP | LDAP | Lightweight Directory Access Protocol |
| 443 | TCP | HTTPS | HTTP Secure (TLS/SSL) |
| 445 | TCP | SMB | Server Message Block – Windows file sharing |
| 465 | TCP | SMTPS | SMTP over TLS (legacy) |
| 514 | UDP | Syslog | System logging messages |
| 587 | TCP | SMTP (Submission) | Modern SMTP submission with STARTTLS |
| 636 | TCP | LDAPS | LDAP over TLS |
| 993 | TCP | IMAPS | IMAP over TLS |
| 995 | TCP | POP3S | POP3 over TLS |
| 1433 | TCP | MSSQL | Microsoft SQL Server |
| 1521 | TCP | Oracle DB | Oracle Database listener |
| 3306 | TCP | MySQL/MariaDB | MySQL/MariaDB database |
| 3389 | TCP | RDP | Remote Desktop Protocol |
| 5060 | TCP/UDP | SIP | Session Initiation Protocol (VoIP) |
| 5061 | TCP | SIPS | SIP over TLS |
| 8080 | TCP | HTTP-Alt | Alternative HTTP / web proxy |

### OSI Model Layers

| Layer | Number | Devices / Protocols |
|-------|--------|---------------------|
| Physical | 1 | Hubs, repeaters, cables, fiber, NIC |
| Data Link | 2 | Switches, bridges, MAC addresses, 802.3, 802.11 |
| Network | 3 | Routers, IP, ICMP, ARP |
| Transport | 4 | TCP, UDP, port numbers |
| Session | 5 | NetBIOS, RPC, SQL sessions |
| Presentation | 6 | TLS/SSL, JPEG, ASCII, encryption/compression |
| Application | 7 | HTTP, FTP, DNS, SMTP, SNMP |

### IP Protocol Numbers

| Number | Protocol | Use |
|--------|----------|-----|
| 1 | ICMP | Ping, traceroute, error messaging |
| 6 | TCP | Reliable, connection-oriented transport |
| 17 | UDP | Fast, connectionless transport |
| 47 | GRE | Generic Routing Encapsulation (VPN tunnels) |
| 50 | ESP | IPsec Encapsulating Security Payload |
| 51 | AH | IPsec Authentication Header |
| 89 | OSPF | Open Shortest Path First routing protocol |

---

## 🔗 Helpful Resources

- [Professor Messer's Free N10-009 Course](https://www.professormesser.com/network-plus/n10-009/n10-009-video/n10-009-training-course/)
- [CompTIA Network+ Exam Objectives (PDF)](https://www.comptia.org/training/resources/exam-objectives)
- [Jason Dion Practice Tests](https://www.diontraining.com/)
- [Subnetting Practice – Subnetting.net](https://subnetting.net/)
- [Cisco Packet Tracer (Free)](https://www.netacad.com/courses/packet-tracer)
- [CompTIANetwork+StudyGuide-N10-004](https://people.computing.clemson.edu/~jmarty/courses/commonCourseContent/NetworkOrSystemsCertifications/CompTIANetwork+StudyGuide-N10-004.pdf)

---

## 📜 License

This repository is for educational purposes. See [LICENSE](./LICENSE) for details.
