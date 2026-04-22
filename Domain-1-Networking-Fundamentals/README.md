# Domain 1 — Networking Fundamentals (23%)

This domain covers the foundational concepts that underpin all networking knowledge. Expect approximately **23%** of exam questions from this domain.

## How to use this page (fast)

1. **Skim the Objective Checklist** and mark what you don’t know.
2. Read the **Core Notes** sections only for weak areas.
3. Do the **Mini-Quiz** (closed book), grade yourself, then review explanations.
4. Run at least one **Lab** (Wireshark + basic host networking commands).
5. Add misses to your repo’s (or personal) **error log** and create flashcards.

---

## ✅ Objective Checklist (Domain 1)

Mark each item as you master it.

### 1.1 Compare and contrast the Open Systems Interconnection (OSI) model layers and encapsulation concepts
- [ ] Map common protocols/technologies to OSI layers
- [ ] Explain encapsulation/decapsulation (PDU names per layer)
- [ ] Explain MTU and fragmentation at a high level

### 1.2 Explain the characteristics of network topologies and network types
- [ ] Compare physical vs logical topology
- [ ] Compare bus/star/ring/mesh/hybrid
- [ ] Compare PAN/LAN/WLAN/MAN/WAN/SAN/SD-WAN and typical use cases

### 1.3 Summarize the types of cables and connectors and explain which is appropriate for a given scenario
- [ ] Identify UTP categories and use cases (Cat5e/Cat6/Cat6a)
- [ ] Compare fiber types (SMF vs MMF) and connectors (LC/SC/ST)
- [ ] Explain attenuation, EMI, crosstalk (NEXT/FEXT), bend radius

### 1.4 Given a scenario, configure a subnet and use appropriate IP addressing schemes
- [ ] Identify public vs private vs special IPv4 ranges
- [ ] Perform quick subnetting (/24–/30 at minimum)
- [ ] Explain default gateway, DNS, DHCP scopes at a practical level

### 1.5 Explain common ports and protocols, their application, and encrypted alternatives
- [ ] Memorize the top ports and match to TCP/UDP
- [ ] Identify secure alternatives (HTTP→HTTPS, Telnet→SSH, etc.)

### 1.6 Explain the use and purpose of network services
- [ ] DNS, DHCP, NTP, AAA (RADIUS/TACACS+), SNMP
- [ ] Understand directory services basics (LDAP/AD) at a high level

### 1.7 Explain basic corporate and datacenter network architecture
- [ ] 2-tier/3-tier, access/distribution/core (conceptual)
- [ ] DMZ purpose and common placements (high level)

> Note: Section numbering is aligned to common Network+ objective structure, but the official exam objective wording can vary by version. Use this checklist as a mastery tracker.

---

## 🧠 Core Notes

### OSI vs TCP/IP models (quick mapping)

| OSI Layer | Name | TCP/IP Layer | Typical Examples |
|---:|---|---|---|
| 7 | Application | Application | HTTP/S, DNS, SMTP, SNMP |
| 6 | Presentation | Application | TLS, JPEG, ASCII |
| 5 | Session | Application | NetBIOS, RPC |
| 4 | Transport | Transport | TCP, UDP |
| 3 | Network | Internet | IP, ICMP |
| 2 | Data Link | Network Access | Ethernet (802.3), Wi‑Fi (802.11), MAC |
| 1 | Physical | Network Access | Copper/fiber, hubs, repeaters |

**Encapsulation (PDU names you should know):**
- L7–L5: **Data**
- L4: **Segment** (TCP) / **Datagram** (UDP)
- L3: **Packet**
- L2: **Frame**
- L1: **Bits**

**Two mnemonics (pick one):**
- 7→1: *Please Do Not Throw Sausage Pizza Away*
- 1→7: *All People Seem To Need Data Processing*

---

### TCP vs UDP (exam-grade)

| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented (3‑way handshake) | Connectionless |
| Reliability | ACKs, retransmits, sequencing | Best-effort |
| Ordering | Guaranteed in-order | Not guaranteed |
| Overhead | Higher | Lower |
| Typical use | HTTPS, SSH, email, file transfer | DNS, DHCP, VoIP, streaming |

**Rule of thumb:**
- If you need **reliability and ordering**, think **TCP**.
- If you need **low latency** and can tolerate loss, think **UDP**.

---

### IPv4 essentials

#### IPv4 classes (legacy concept; still tested for recognition)

| Class | Range | Default Mask | Typical Use |
|---|---|---|---|
| A | 1.0.0.0 – 126.255.255.255 | /8 | Large networks |
| B | 128.0.0.0 – 191.255.255.255 | /16 | Medium networks |
| C | 192.0.0.0 – 223.255.255.255 | /24 | Small networks |
| D | 224.0.0.0 – 239.255.255.255 | N/A | Multicast |
| E | 240.0.0.0 – 255.255.255.255 | N/A | Reserved |

#### Private (RFC 1918) ranges

| Range | CIDR | Notes |
|---|---|---|
| 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 | “Class A private” |
| 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 | “Class B private” |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 | “Class C private” |

#### Special IPv4 addresses

| Address | Purpose |
|---|---|
| 127.0.0.1 | Loopback |
| 169.254.x.x | APIPA (self-assigned; often DHCP failure clue) |
| 0.0.0.0 | Unspecified / default route |
| 255.255.255.255 | Limited broadcast |

#### CIDR quick reference (/24–/30)

| CIDR | Mask | Usable Hosts |
|---:|---|---:|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /29 | 255.255.255.248 | 6 |
| /30 | 255.255.255.252 | 2 |

> See `../Resources/subnetting-cheatsheet.md` for deeper subnetting drills.

---

### IPv6 essentials

- IPv6 addresses are **128-bit**, written as eight groups of four hex digits.
- Shorthand rules:
  1. Drop **leading zeros** in a group (`0db8` → `db8`)
  2. Replace **one** contiguous run of all-zero groups with `::` (only once)

| IPv6 Type | Prefix | Description |
|---|---|---|
| Global Unicast | 2000::/3 | Publicly routable |
| Link-Local | FE80::/10 | Same-link only, auto-configured |
| Loopback | ::1/128 | Equivalent to 127.0.0.1 |
| Multicast | FF00::/8 | One-to-many |
| Unique Local | FC00::/7 | Private-style addressing |

#### IPv6 transition technologies

| Technology | Description |
|---|---|
| Dual stack | Run IPv4 and IPv6 simultaneously |
| Tunneling (6in4) | Encapsulate IPv6 inside IPv4 |
| NAT64 | Translate between IPv6 and IPv4 |

---

### Network topologies (what exam questions often look like)

#### Physical topologies

| Topology | Description | Pros | Cons |
|---|---|---|---|
| Bus | Single shared cable | Simple, cheap | Collisions; single point of failure |
| Star | Central switch/hub | Easy to manage; fault isolation | Central device failure impacts network |
| Ring | Circular loop (token passing) | Predictable performance | Break can impact whole ring |
| Mesh | Many interconnections | High redundancy | Expensive/complex |
| Hybrid | Combination | Flexible | Complex |

#### Logical topologies (common associations)
- **Bus:** classic Ethernet (802.3) on shared media
- **Ring:** Token Ring / FDDI concepts
- **Star:** modern switched Ethernet (unicast switching)

#### Wireless modes

| Mode | Description |
|---|---|
| Infrastructure | Clients connect via AP (WAP) |
| Ad hoc / IBSS | Device-to-device, no AP |
| Mesh | Multiple APs form self-healing mesh |

---

### Network types (quick compare)

| Type | Scope | Example |
|---|---|---|
| PAN | Personal (~10m) | Bluetooth, USB tethering |
| LAN | Building/floor | Office Ethernet |
| WLAN | Wireless LAN | Wi‑Fi (802.11) |
| MAN | City/campus | Metro Ethernet |
| WAN | Regional/global | MPLS, leased lines, Internet |
| SAN | Storage network | Fibre Channel, iSCSI |
| SD‑WAN | Overlay WAN | Centralized WAN policy + multiple links |

---

## 🔌 Ports & protocols (quick-hit set)

Use `../Resources/common-ports.md` as your master list, but you should have these instant-recall:

| Service | Port | Transport | Secure Alternative / Notes |
|---|---:|---|---|
| HTTP | 80 | TCP | HTTPS 443 |
| HTTPS | 443 | TCP | TLS |
| DNS | 53 | UDP/TCP | UDP common; TCP for zone transfers/large responses |
| DHCP | 67/68 | UDP | Server 67, client 68 |
| SSH | 22 | TCP | Secure remote admin |
| Telnet | 23 | TCP | Replace with SSH |
| SMTP | 25 | TCP | SMTPS 465 / Submission 587 (varies by org) |
| IMAP | 143 | TCP | IMAPS 993 |
| POP3 | 110 | TCP | POP3S 995 |
| SNMP | 161/162 | UDP | Prefer SNMPv3 |
| NTP | 123 | UDP | Time sync |
| RDP | 3389 | TCP/UDP | Remote desktop |

---

## 🧪 Labs (do at least one per week)

### Lab 1 — OSI in the real world with `ping`, `tracert/traceroute`, and DNS
**Goal:** connect commands to OSI layers and isolate where failures live.

1. Run `ipconfig /all` (Windows) or `ifconfig`/`ip a` (Linux/macOS) and record:
   - IP address, subnet mask/prefix
   - default gateway
   - DNS servers
2. `ping` your default gateway.
3. `ping 8.8.8.8` (tests L3 reachability beyond LAN).
4. `ping example.com` (tests DNS + reachability).
5. Run `tracert example.com` (Windows) or `traceroute example.com` (Linux/macOS).

**Write-up prompts (add to your notes):**
- If `ping 8.8.8.8` works but `ping example.com` fails, what is the likely issue?
- Which OSI layers are involved in each step?

### Lab 2 — Wireshark: DHCP DORA and DNS resolution
**Goal:** recognize DHCP and DNS traffic and fields.

1. Start Wireshark capture on your active interface.
2. Renew your DHCP lease.
3. Filter: `dhcp` and identify **Discover, Offer, Request, Ack**.
4. Filter: `dns` and resolve a domain.

**Checkpoints:**
- Identify the DHCP server IP.
- Identify your assigned IP and lease time.
- Confirm DNS query type (A/AAAA) and response.

### Lab 3 — Subnetting drill (paper + verify)
**Goal:** become fast at /24–/30.

For each network below, write:
- network address
- first/last usable
- broadcast
- number of usable hosts

Networks:
- 192.168.10.0/26
- 10.0.5.128/25
- 172.16.12.64/27

---

## 📝 Mini-Quiz (20 questions)

**Rules:** closed book, 20 minutes max.

1. Which OSI layer is responsible for routing packets between networks?
2. What PDU name is used at OSI Layer 2?
3. Name the three steps of the TCP 3‑way handshake.
4. Give two protocols that commonly use UDP.
5. Which IPv4 range is APIPA and what does it usually indicate?
6. What is the difference between a physical and logical topology?
7. Which topology provides the highest redundancy but is typically the most expensive?
8. What is the default subnet mask for a Class C network?
9. How many usable hosts are in a /27 subnet?
10. In IPv6, what does `::` represent and how many times can it be used in one address?
11. What is the IPv6 link-local prefix?
12. Which port does DNS use and why might it use TCP sometimes?
13. What is the client port used in DHCP?
14. Which port is used for SSH?
15. What secure protocol typically replaces Telnet?
16. What is the purpose of a default gateway?
17. If you can ping an IP address but not a hostname, what is the likely problem?
18. Which network type is typically used for storage traffic?
19. What is SD‑WAN in one sentence?
20. Name one benefit of TCP and one benefit of UDP.

### Answer key (brief explanations)
1. Layer 3 (Network)
2. Frame
3. SYN, SYN‑ACK, ACK
4. DNS, DHCP (also VoIP, streaming)
5. 169.254.0.0/16; usually indicates DHCP failure/unavailable
6. Physical = wiring layout; logical = how traffic flows
7. Mesh
8. 255.255.255.0 (/24)
9. 30
10. A run of consecutive all‑zero groups; only once
11. FE80::/10
12. 53; TCP for zone transfers/large responses
13. UDP 68 (server UDP 67)
14. 22/TCP
15. SSH
16. Route to other networks (off‑subnet)
17. DNS issue (wrong DNS server, failure resolving)
18. SAN
19. Centralized control of WAN links using an overlay and policies
20. TCP: reliability/ordering; UDP: low overhead/latency

---

## ✅ Study Checklist (daily/weekly)

- [ ] Memorize OSI layers + PDUs + 2 examples per layer
- [ ] Be able to do /24–/30 subnetting without a calculator
- [ ] Know private/special IPv4 ranges instantly
- [ ] Know link-local/loopback/multicast IPv6 ranges
- [ ] Drill top ports daily (5–10 minutes)
- [ ] Run 1 lab per week and write a short summary

---

## 🔗 Related resources in this repo

- Subnetting cheat sheet: `../Resources/subnetting-cheatsheet.md`
- Common ports: `../Resources/common-ports.md`
- CLI commands: `../Resources/cli-commands.md`