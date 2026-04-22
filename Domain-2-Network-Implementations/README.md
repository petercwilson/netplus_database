# Domain 2 — Network Implementations (20%)

This domain focuses on deploying and configuring network hardware and protocols, including routers, switches, and wireless infrastructure. Expect approximately **20%** of exam questions from this domain.

## How to use this page (fast)

1. **Skim the Objective Checklist** and mark what you don’t know.
2. Read the **Core Notes** sections only for weak areas.
3. Do the **Mini-Quiz** (closed book), grade yourself, then review explanations.
4. Run at least one **Lab** (Packet Tracer + verification commands, and optionally Wireshark).
5. Add misses to your repo’s (or personal) **error log** and create flashcards.

---

## ✅ Objective Checklist (Domain 2)

### 2.1 Routing
- [ ] Describe static routes vs. dynamic routes
- [ ] Explain default routes (0.0.0.0/0)
- [ ] Compare common routing protocols (RIP, OSPF, EIGRP, BGP) at a high level
- [ ] Explain administrative distance (AD) vs. metric
- [ ] Describe NAT vs. PAT and when you’d use each

### 2.2 Switching
- [ ] Explain how a switch learns MAC addresses and forwards frames
- [ ] Configure access vs. trunk ports (802.1Q tagging)
- [ ] Explain native VLAN risk (avoid VLAN 1)
- [ ] Explain STP purpose and identify the root bridge
- [ ] Explain why EtherChannel/LAG is used and what LACP does

### 2.3 Wireless
- [ ] Compare 802.11 a/b/g/n/ac/ax/be by band and typical use
- [ ] Choose WPA2 vs WPA3 and explain why WEP/WPA are legacy
- [ ] Know 2.4 GHz non-overlapping channels (1/6/11)
- [ ] Explain SSID vs BSSID, and what roaming means

### 2.4 Cables & other implementations
- [ ] Select correct twisted-pair category (Cat5e/Cat6/Cat6a/Cat8) for a scenario
- [ ] Explain SMF vs MMF and typical distances

---

## 🧠 Core Notes

## 📚 Key Topics

### 2.1 Routing

#### Routing Concepts

| Term | Definition |
|------|-----------|
| Static Route | Manually configured path; no overhead, no adaptability |
| Default Route | Gateway of last resort (0.0.0.0/0) |
| Dynamic Route | Automatically learned via a routing protocol |
| Administrative Distance (AD) | Trustworthiness of a route source (lower = preferred) |
| Metric | Cost used within a protocol to choose the best path |

#### Common Routing Protocols

| Protocol | Type | AD | Metric | Notes |
|----------|------|----|--------|-------|
| RIP v2 | Distance Vector | 120 | Hop count (max 15) | Legacy; slow convergence |
| OSPF | Link State | 110 | Cost (bandwidth) | Fast convergence; areas |
| EIGRP | Hybrid (Cisco) | 90 | Bandwidth + delay | Cisco proprietary (now open) |
| BGP | Path Vector | 20 (eBGP) / 200 (iBGP) | AS path | Internet routing protocol |
| IS-IS | Link State | 115 | Cost | Common in ISP cores |

#### NAT Types

| Type | Description |
|------|-------------|
| Static NAT | One-to-one mapping (public ↔ private) |
| Dynamic NAT | Pool of public IPs assigned dynamically |
| PAT / NAT Overload | Many-to-one; uses ports to distinguish sessions (most common) |

---

### 2.2 Switching

#### Switch Operation

1. **MAC Address Learning** — When a frame arrives, the switch records source MAC + port in the MAC table.
2. **Forwarding** — If destination MAC is known, send to that port only (unicast).
3. **Flooding** — If destination MAC is unknown, send to all ports except source (unknown unicast / broadcast).

#### VLANs (Virtual LANs)

| Concept | Description |
|---------|-------------|
| VLAN | Logical segmentation of a switch; separates broadcast domains |
| Access Port | Carries traffic for a single VLAN (end-device connection) |
| Trunk Port | Carries traffic for multiple VLANs using 802.1Q tagging |
| Native VLAN | Untagged VLAN on a trunk (default VLAN 1 — change this!) |
| Inter-VLAN Routing | Requires a router or Layer 3 switch |

#### Spanning Tree Protocol (STP)

| Term | Description |
|------|-------------|
| STP (802.1D) | Prevents Layer 2 loops; elects root bridge |
| RSTP (802.1w) | Rapid STP; much faster convergence |
| Port States | Blocking → Listening → Learning → Forwarding (STP) |
| BPDU | Bridge Protocol Data Unit — STP control message |
| Root Bridge | Switch with the lowest Bridge ID (priority + MAC) |

#### EtherChannel / Link Aggregation

- Combines multiple physical links into one logical link.
- **LACP** (802.3ad) — Open standard
- **PAgP** — Cisco proprietary
- Provides redundancy and increased bandwidth.

---

### 2.3 Wireless Networking

#### 802.11 Standards

| Standard | Band | Max Speed | Notes |
|----------|------|-----------|-------|
| 802.11a | 5 GHz | 54 Mbps | Less interference; shorter range |
| 802.11b | 2.4 GHz | 11 Mbps | Longer range; crowded band |
| 802.11g | 2.4 GHz | 54 Mbps | Backward compatible with b |
| 802.11n (Wi‑Fi 4) | 2.4 / 5 GHz | 600 Mbps | MIMO; dual-band |
| 802.11ac (Wi‑Fi 5) | 5 GHz | ~3.5 Gbps | MU‑MIMO; beamforming |
| 802.11ax (Wi‑Fi 6/6E) | 2.4 / 5 / 6 GHz | ~9.6 Gbps | OFDMA; improved density |
| 802.11be (Wi‑Fi 7) | 2.4 / 5 / 6 GHz | ~46 Gbps | Multi‑link operation |

#### Wireless Security

| Protocol | Notes |
|----------|-------|
| WEP | Deprecated; easily cracked — do not use |
| WPA | Improved over WEP (TKIP); still vulnerable |
| WPA2 | CCMP/AES; current minimum standard |
| WPA3 | SAE handshake; strongest; protects open networks |
| 802.1X / EAP | Enterprise authentication (RADIUS back-end) |

#### Wireless Channels (2.4 GHz Non‑Overlapping)

- **Channels 1, 6, 11** — Use these to avoid interference in 2.4 GHz deployments.
- 5 GHz has more non-overlapping channels (36, 40, 44, 48, etc.).

#### Wireless Concepts

| Term | Definition |
|------|-----------|
| SSID | Service Set Identifier — network name |
| BSSID | MAC address of the WAP |
| CSMA/CA | Collision avoidance mechanism for wireless |
| RTS/CTS | Request to Send / Clear to Send — handles hidden node problem |
| Roaming | Client moves between WAPs within the same network |
| BSS | Basic Service Set — single WAP + clients |
| ESS | Extended Service Set — multiple WAPs, same SSID |

---

### 2.4 Other Network Implementations

#### Cable Types

| Type | Max Distance | Speed | Notes |
|------|-------------|-------|-------|
| Cat 5e | 100 m | 1 Gbps | Minimum for modern LANs |
| Cat 6 | 100 m (55 m @ 10G) | 10 Gbps | Reduced crosstalk |
| Cat 6a | 100 m | 10 Gbps | Augmented; better shielding |
| Cat 7 | 100 m | 10 Gbps | Shielded; less common |
| Cat 8 | 30 m | 40 Gbps | Data center use |
| Fiber (SMF) | Km range | 100 Gbps+ | Long distance; single mode |
| Fiber (MMF) | ~550 m | 10 Gbps | Shorter distance; multi mode |

---

## 🧪 Mini-Quiz (Domain 2)

1) Which value is preferred: lower or higher administrative distance?
2) What does a default route of `0.0.0.0/0` represent?
3) What’s the difference between NAT and PAT?
4) What does STP prevent?
5) Which 2.4 GHz Wi‑Fi channels are non-overlapping in most regions?

### Answer key
1) Lower.
2) Gateway of last resort (matches any destination not in the routing table).
3) NAT translates addresses; PAT translates addresses *and* ports (many-to-one).
4) Layer 2 switching loops.
5) 1, 6, 11.

---

## 🧪 Labs (recommended)

> Mix of Packet Tracer + Wireshark (optional) per your preference.

### Packet Tracer labs
- Build a small LAN with two VLANs + trunk port; verify VLAN membership and trunking.
- Configure an EtherChannel using LACP; verify the bundle is up.
- Trigger/observe STP behavior (root bridge selection, blocked port).

### Wireshark labs (optional)
- Capture DHCP + DNS traffic; identify packets and ports used.

---

## 🔗 Related Resources

- [CLI Commands](../Resources/cli-commands.md)
- [Common Ports](../Resources/common-ports.md)
- [Labs](../Labs/README.md)