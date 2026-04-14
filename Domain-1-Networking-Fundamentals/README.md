# Domain 1 – Networking Fundamentals (23%)

This domain covers the foundational concepts that underpin all networking knowledge. Expect approximately **23%** of exam questions from this domain.

---

## 📚 Key Topics

### 1.1 OSI and TCP/IP Models

| OSI Layer | Name | TCP/IP Layer | Protocols / Examples |
|-----------|------|--------------|----------------------|
| 7 | Application | Application | HTTP, FTP, DNS, SMTP, SNMP |
| 6 | Presentation | Application | TLS, JPEG, ASCII |
| 5 | Session | Application | NetBIOS, RPC |
| 4 | Transport | Transport | TCP, UDP |
| 3 | Network | Internet | IP, ICMP, ARP |
| 2 | Data Link | Network Access | Ethernet (802.3), Wi-Fi (802.11), MAC |
| 1 | Physical | Network Access | Cables, hubs, repeaters, fiber |

**Mnemonic (Layers 7→1):** _Please Do Not Throw Sausage Pizza Away_  
**Mnemonic (Layers 1→7):** _All People Seem To Need Data Processing_

#### TCP vs UDP

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented (3-way handshake) | Connectionless |
| Reliability | Guaranteed delivery, ACKs | No guarantees |
| Speed | Slower (overhead) | Faster (low overhead) |
| Use cases | HTTP/S, FTP, SSH, email | DNS, DHCP, TFTP, VoIP, streaming |

---

### 1.2 IPv4 Addressing

#### IPv4 Address Classes

| Class | Range | Default Subnet Mask | Use |
|-------|-------|---------------------|-----|
| A | 1.0.0.0 – 126.255.255.255 | /8 (255.0.0.0) | Large networks |
| B | 128.0.0.0 – 191.255.255.255 | /16 (255.255.0.0) | Medium networks |
| C | 192.0.0.0 – 223.255.255.255 | /24 (255.255.255.0) | Small networks |
| D | 224.0.0.0 – 239.255.255.255 | N/A | Multicast |
| E | 240.0.0.0 – 255.255.255.255 | N/A | Reserved/Experimental |

#### Private (RFC 1918) Address Ranges

| Range | CIDR | Notes |
|-------|------|-------|
| 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 | Class A private |
| 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 | Class B private |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 | Class C private |

#### Special IPv4 Addresses

| Address | Purpose |
|---------|---------|
| 127.0.0.1 | Loopback (localhost) |
| 169.254.x.x | APIPA (Automatic Private IP Addressing) |
| 255.255.255.255 | Limited broadcast |
| 0.0.0.0 | Unspecified / default route |

#### CIDR & Subnetting Quick Reference

| CIDR | Subnet Mask | Hosts per Subnet |
|------|-------------|-----------------|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /29 | 255.255.255.248 | 6 |
| /30 | 255.255.255.252 | 2 |

> See [`/Resources/subnetting-cheatsheet.md`](../Resources/subnetting-cheatsheet.md) for the full subnetting reference.

---

### 1.3 IPv6 Addressing

- **128-bit** addresses written in eight groups of four hex digits separated by colons.  
  Example: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
- **Shorthand rules:**
  1. Drop leading zeros in a group: `0db8` → `db8`
  2. Replace one contiguous run of all-zero groups with `::` (only once)

| IPv6 Type | Prefix | Description |
|-----------|--------|-------------|
| Global Unicast | 2000::/3 | Publicly routable (like public IPv4) |
| Link-Local | FE80::/10 | Same link only (auto-configured) |
| Loopback | ::1/128 | Equivalent to 127.0.0.1 |
| Multicast | FF00::/8 | One-to-many delivery |
| Unique Local | FC00::/7 | Private (like RFC 1918) |

#### IPv6 Transition Technologies

| Technology | Description |
|------------|-------------|
| Dual Stack | Device runs both IPv4 and IPv6 simultaneously |
| Tunneling (6in4) | IPv6 packets encapsulated inside IPv4 |
| NAT64 | Translates between IPv6 and IPv4 |

---

### 1.4 Network Topologies

#### Physical Topologies

| Topology | Description | Pros | Cons |
|----------|-------------|------|------|
| Bus | All devices on a single cable | Simple, cheap | Single point of failure; collisions |
| Star | All devices connect to a central switch/hub | Easy to manage; fault isolation | Central device failure kills network |
| Ring | Devices in a circular loop (Token Ring) | Predictable performance | Single break can fail entire ring |
| Mesh | Every device connected to every other | High redundancy | Expensive; complex cabling |
| Hybrid | Combination of topologies | Flexible | Complex |

#### Logical Topologies

- **Bus:** Ethernet (802.3) – shared medium logic  
- **Ring:** Token Ring, FDDI – token passing logic  
- **Star:** Modern switched Ethernet – switched unicast logic

#### Wireless Topologies

| Mode | Description |
|------|-------------|
| Infrastructure | Devices connect to a Wireless Access Point (WAP) |
| Ad hoc / IBSS | Direct device-to-device, no WAP |
| Mesh | Multiple WAPs form a self-healing wireless mesh |

---

### 1.5 Network Types and Characteristics

| Type | Scope | Example |
|------|-------|---------|
| PAN | Personal (~10 m) | Bluetooth, USB |
| LAN | Building/floor | Office Ethernet |
| MAN | City/campus | Metro Ethernet, municipal Wi-Fi |
| WAN | Country/global | Internet, MPLS, leased lines |
| WLAN | Wireless LAN | Wi-Fi (802.11) |
| SAN | Storage network | Fibre Channel, iSCSI |
| SDWAN | Software-defined WAN | Overlay WAN management |

---

## ✅ Study Checklist

- [ ] Memorize all 7 OSI layers and their functions
- [ ] Explain the difference between TCP and UDP with examples
- [ ] Calculate usable hosts from a given CIDR notation
- [ ] Identify private vs. public vs. special IPv4 addresses
- [ ] Describe IPv6 address types and transition technologies
- [ ] Compare physical and logical topologies
- [ ] Know when to use different network types (LAN, WAN, etc.)

---

## 🔗 Related Resources

- [Subnetting Cheat Sheet](../Resources/subnetting-cheatsheet.md)
- [Common Ports Reference](../Resources/common-ports.md)
- [CLI Commands](../Resources/cli-commands.md)
