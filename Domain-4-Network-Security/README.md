# Domain 4 – Network Security (20%)

This domain covers protecting the network from threats through hardening, understanding attacks, and applying modern security frameworks such as Zero Trust. Expect approximately **20%** of exam questions from this domain.

---

## 📚 Key Topics

### 4.1 Network Hardening

#### Device Hardening Best Practices

| Practice | Description |
|----------|-------------|
| Change default credentials | Never use manufacturer default usernames/passwords |
| Disable unused services | Reduce attack surface (e.g., disable Telnet, HTTP management) |
| Enable SSH instead of Telnet | Encrypt management sessions |
| Apply patches/updates | Remediate known vulnerabilities |
| Enable logging | Send logs to centralized syslog server |
| Use ACLs | Restrict who can reach management interfaces |
| Port security | Limit which MAC addresses can connect to a switch port |
| BPDU Guard | Prevents rogue switches from becoming STP root |
| DHCP Snooping | Blocks rogue DHCP servers on switch ports |
| Dynamic ARP Inspection (DAI) | Prevents ARP poisoning/spoofing |
| 802.1X (NAC) | Requires authentication before network access |

#### Firewall Types

| Type | Description |
|------|-------------|
| Packet Filter | Inspects individual packets (stateless); L3/L4 |
| Stateful Inspection | Tracks connection state; understands context |
| Application (Layer 7) | Inspects application data; proxy-based |
| NGFW | Next-Generation Firewall; IPS + App awareness + SSL inspection |
| WAF | Web Application Firewall; protects HTTP/S apps |

#### Network Segmentation

| Method | Description |
|--------|-------------|
| DMZ | Demilitarized zone; hosts public-facing servers isolated from internal LAN |
| VLAN | Logical segmentation at Layer 2 |
| Screened Subnet | Similar to DMZ; uses two firewalls |
| Air Gap | Physical isolation; no network connection |
| Microsegmentation | Fine-grained segmentation (often in SDN/cloud) |

---

### 4.2 Common Network Attacks

#### Reconnaissance Attacks

| Attack | Description |
|--------|-------------|
| Port Scanning | Identifies open ports and services (e.g., nmap) |
| Ping Sweep | Finds live hosts on a network |
| OS Fingerprinting | Determines OS via packet analysis |
| Packet Sniffing | Captures network traffic (passive) |

#### Denial of Service (DoS / DDoS)

| Attack | Description |
|--------|-------------|
| Flood (SYN, UDP, ICMP) | Overwhelms target with traffic |
| Ping of Death | Malformed oversized ICMP packet |
| Smurf | Amplified ICMP broadcast flood |
| DDoS | Distributed DoS using botnets |
| Amplification (DNS, NTP) | Small requests → large responses directed at victim |

#### Man-in-the-Middle (MitM) Attacks

| Attack | Description |
|--------|-------------|
| ARP Poisoning | Associates attacker's MAC with a victim's IP |
| DNS Spoofing / Poisoning | Returns false DNS responses |
| SSL Stripping | Downgrades HTTPS to HTTP |
| Evil Twin | Rogue AP mimicking legitimate SSID |
| Session Hijacking | Steals session tokens |

#### Social Engineering

| Attack | Description |
|--------|-------------|
| Phishing | Fraudulent email to steal credentials |
| Spear Phishing | Targeted phishing at specific individuals |
| Vishing | Voice/phone phishing |
| Smishing | SMS phishing |
| Tailgating / Piggybacking | Following authorized person through secured door |

#### Other Attacks

| Attack | Description |
|--------|-------------|
| VLAN Hopping | Switch spoofing or double-tagging to access other VLANs |
| DHCP Starvation | Exhausts DHCP pool with fake requests |
| Rogue DHCP Server | Attacker's DHCP server assigns malicious gateway/DNS |
| Password Cracking | Brute force, dictionary, rainbow table attacks |
| Ransomware | Encrypts data and demands payment |

---

### 4.3 Zero Trust Architecture

> **Core Principle:** _"Never trust, always verify."_ No user, device, or network location is trusted by default — even inside the corporate network.

#### Zero Trust Pillars

| Pillar | Description |
|--------|-------------|
| Identity | Verify every user with strong authentication (MFA) |
| Devices | Ensure devices meet health/compliance before access |
| Network | Microsegment; limit lateral movement |
| Applications | Authenticate access to each app individually |
| Data | Classify and protect data; encrypt at rest and in transit |

#### Zero Trust vs. Traditional Perimeter Security

| Aspect | Traditional (Castle-and-Moat) | Zero Trust |
|--------|-------------------------------|-----------|
| Trust model | Trust everything inside the perimeter | Trust nothing, verify everything |
| Lateral movement | Easy once inside | Prevented by microsegmentation |
| Remote users | VPN into trusted network | Identity + device-aware access |
| Insider threats | Difficult to detect | Continuously validated |

---

### 4.4 VPNs and Encryption

#### VPN Types

| Type | Description |
|------|-------------|
| Site-to-Site VPN | Connects two networks (e.g., branch to HQ) |
| Remote Access VPN | Individual users connect to corporate network |
| SSL/TLS VPN | Browser-based or client; uses HTTPS |
| IPsec VPN | Layer 3 tunneling; uses ESP and AH |
| Split Tunneling | Only some traffic goes through VPN |
| Full Tunneling | All traffic routed through VPN |

#### IPsec Modes

| Mode | Description |
|------|-------------|
| Transport | Encrypts payload only; original headers intact |
| Tunnel | Encrypts entire original packet; new header added |

#### Encryption Protocols

| Protocol | Use Case |
|----------|---------|
| AES | Symmetric encryption; industry standard |
| RSA | Asymmetric; key exchange, digital signatures |
| TLS | Secures application-layer communications |
| SHA-256/512 | Hashing for integrity verification |

---

### 4.5 Authentication and Access Control

| Concept | Description |
|---------|-------------|
| AAA | Authentication, Authorization, Accounting |
| RADIUS | Centralizes AAA; UDP 1812/1813 |
| TACACS+ | Cisco AAA; TCP 49; separates auth/authz/accounting |
| 802.1X | Port-based NAC; uses EAP |
| MFA | Multi-Factor Authentication; something you know/have/are |
| RBAC | Role-Based Access Control |
| LDAP / AD | Directory services for user authentication |

---

## ✅ Study Checklist

- [ ] List at least 5 device hardening best practices
- [ ] Explain the difference between stateful and stateless firewalls
- [ ] Describe ARP poisoning and how DAI prevents it
- [ ] Explain the Zero Trust principle and its pillars
- [ ] Compare site-to-site and remote-access VPNs
- [ ] Explain IPsec tunnel vs. transport mode
- [ ] Describe the difference between RADIUS and TACACS+
- [ ] Identify social engineering attack types

---

## 🔗 Related Resources

- [CLI Commands](../Resources/cli-commands.md)
- [Labs](../Labs/README.md)
