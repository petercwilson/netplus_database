# Common Ports & Protocols – Cheat Sheet

A comprehensive port reference for CompTIA Network+ N10-009.

---

## Well-Known Ports (0–1023)

| Port | Protocol | Service | Description |
|------|----------|---------|-------------|
| 20 | TCP | FTP-DATA | File Transfer Protocol – data channel |
| 21 | TCP | FTP | File Transfer Protocol – control channel |
| 22 | TCP | SSH / SFTP / SCP | Secure Shell; encrypted remote access |
| 23 | TCP | Telnet | Unencrypted remote terminal – **avoid** |
| 25 | TCP | SMTP | Simple Mail Transfer Protocol – sending email |
| 53 | TCP/UDP | DNS | Domain Name System |
| 67 | UDP | DHCP (Server) | DHCP server listens here |
| 68 | UDP | DHCP (Client) | DHCP client listens here |
| 69 | UDP | TFTP | Trivial File Transfer Protocol |
| 80 | TCP | HTTP | Web traffic (unencrypted) |
| 110 | TCP | POP3 | Post Office Protocol v3 |
| 119 | TCP | NNTP | Network News Transfer Protocol |
| 123 | UDP | NTP | Network Time Protocol |
| 143 | TCP | IMAP | Internet Message Access Protocol |
| 161 | UDP | SNMP | SNMP queries (manager → agent) |
| 162 | UDP | SNMP Trap | SNMP traps (agent → manager) |
| 389 | TCP/UDP | LDAP | Lightweight Directory Access Protocol |
| 443 | TCP | HTTPS | HTTP over TLS/SSL |
| 445 | TCP | SMB | Server Message Block – Windows file sharing |
| 465 | TCP | SMTPS | SMTP over TLS (older standard) |
| 514 | UDP | Syslog | System logging |
| 587 | TCP | SMTP Submission | Modern SMTP with STARTTLS |
| 636 | TCP | LDAPS | LDAP over TLS |
| 993 | TCP | IMAPS | IMAP over TLS |
| 995 | TCP | POP3S | POP3 over TLS |

---

## Registered Ports (1024–49151)

| Port | Protocol | Service | Description |
|------|----------|---------|-------------|
| 1433 | TCP | MSSQL | Microsoft SQL Server |
| 1521 | TCP | Oracle DB | Oracle Database listener |
| 1720 | TCP | H.323 | VoIP call signaling |
| 1812 | UDP | RADIUS Auth | RADIUS authentication |
| 1813 | UDP | RADIUS Acct | RADIUS accounting |
| 3306 | TCP | MySQL / MariaDB | MySQL/MariaDB database |
| 3389 | TCP | RDP | Remote Desktop Protocol |
| 5060 | TCP/UDP | SIP | Session Initiation Protocol (VoIP) |
| 5061 | TCP | SIPS | SIP over TLS |
| 8080 | TCP | HTTP-Alt | Alternate HTTP / proxy |
| 8443 | TCP | HTTPS-Alt | Alternate HTTPS |
| 49 | TCP | TACACS+ | Cisco AAA protocol |

---

## Protocol Numbers (IP Header)

| Number | Protocol | Description |
|--------|----------|-------------|
| 1 | ICMP | Internet Control Message Protocol |
| 6 | TCP | Transmission Control Protocol |
| 17 | UDP | User Datagram Protocol |
| 47 | GRE | Generic Routing Encapsulation |
| 50 | ESP | IPsec Encapsulating Security Payload |
| 51 | AH | IPsec Authentication Header |
| 89 | OSPF | Open Shortest Path First |

---

## TCP vs UDP Service Summary

| Category | TCP Services | UDP Services |
|----------|-------------|-------------|
| Web | HTTP (80), HTTPS (443) | – |
| Email | SMTP (25, 587), POP3 (110), IMAP (143), + TLS variants | – |
| File Transfer | FTP (20, 21), SFTP (22), SMB (445) | TFTP (69) |
| Remote Access | SSH (22), Telnet (23), RDP (3389) | – |
| Name Resolution | DNS (53) TCP for zone transfers | DNS (53) UDP for queries |
| Network Mgmt | LDAP (389), LDAPS (636) | SNMP (161/162), NTP (123), Syslog (514), DHCP (67/68) |
| VoIP | SIP (5060/5061), H.323 (1720) | SIP (5060), RTP (dynamic) |
| Authentication | TACACS+ (49), RADIUS (1812/1813) | RADIUS (1812/1813) |

---

## Memory Tips

| Trick | Ports |
|-------|-------|
| **"FTP splits at 20/21"** | 20 = data, 21 = control |
| **"SSH, SCP, SFTP all ride on 22"** | One port, three services |
| **"DNS is both TCP and UDP 53"** | UDP for queries, TCP for zone transfers |
| **"DHCP: 67 serves, 68 receives"** | Server=67, Client=68 |
| **"SNMP: 161 asks, 162 tells"** | 161 = polls, 162 = traps |
| **"Secure versions add ~450–800"** | IMAPS=993, POP3S=995, LDAPS=636, HTTPS=443 |
