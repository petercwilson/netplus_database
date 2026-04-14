# Domain 2 – Network Implementations (20%)

This domain focuses on deploying and configuring network hardware and protocols, including routers, switches, and wireless infrastructure. Expect approximately **20%** of exam questions from this domain.

---

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

1. **MAC Address Learning** – When a frame arrives, the switch records source MAC + port in the MAC table.
2. **Forwarding** – If destination MAC is known, send to that port only (unicast).
3. **Flooding** – If destination MAC is unknown, send to all ports except source (unknown unicast / broadcast).

#### VLANs (Virtual LANs)

| Concept | Description |
|---------|-------------|
| VLAN | Logical segmentation of a switch; separates broadcast domains |
| Access Port | Carries traffic for a single VLAN (end-device connection) |
| Trunk Port | Carries traffic for multiple VLANs using 802.1Q tagging |
| Native VLAN | Untagged VLAN on a trunk (default VLAN 1 – change this!) |
| Inter-VLAN Routing | Requires a router or Layer 3 switch |

#### Spanning Tree Protocol (STP)

| Term | Description |
|------|-------------|
| STP (802.1D) | Prevents Layer 2 loops; elects root bridge |
| RSTP (802.1w) | Rapid STP; much faster convergence |
| Port States | Blocking → Listening → Learning → Forwarding (STP) |
| BPDU | Bridge Protocol Data Unit – STP control message |
| Root Bridge | Switch with the lowest Bridge ID (priority + MAC) |

#### EtherChannel / Link Aggregation

- Combines multiple physical links into one logical link.
- **LACP** (802.3ad) – Open standard  
- **PAgP** – Cisco proprietary  
- Provides redundancy and increased bandwidth.

---

### 2.3 Wireless Networking

#### 802.11 Standards

| Standard | Band | Max Speed | Notes |
|----------|------|-----------|-------|
| 802.11a | 5 GHz | 54 Mbps | Less interference; shorter range |
| 802.11b | 2.4 GHz | 11 Mbps | Longer range; crowded band |
| 802.11g | 2.4 GHz | 54 Mbps | Backward compatible with b |
| 802.11n (Wi-Fi 4) | 2.4 / 5 GHz | 600 Mbps | MIMO; dual-band |
| 802.11ac (Wi-Fi 5) | 5 GHz | ~3.5 Gbps | MU-MIMO; beamforming |
| 802.11ax (Wi-Fi 6/6E) | 2.4 / 5 / 6 GHz | ~9.6 Gbps | OFDMA; improved density |
| 802.11be (Wi-Fi 7) | 2.4 / 5 / 6 GHz | ~46 Gbps | Multi-link operation |

#### Wireless Security

| Protocol | Notes |
|----------|-------|
| WEP | Deprecated; easily cracked – do not use |
| WPA | Improved over WEP (TKIP); still vulnerable |
| WPA2 | CCMP/AES; current minimum standard |
| WPA3 | SAE handshake; strongest; protects open networks |
| 802.1X / EAP | Enterprise authentication (RADIUS back-end) |

#### Wireless Channels (2.4 GHz Non-Overlapping)

- **Channels 1, 6, 11** – Use these to avoid interference in 2.4 GHz deployments.
- 5 GHz has more non-overlapping channels (36, 40, 44, 48, etc.).

#### Wireless Concepts

| Term | Definition |
|------|-----------|
| SSID | Service Set Identifier – network name |
| BSSID | MAC address of the WAP |
| CSMA/CA | Collision avoidance mechanism for wireless |
| RTS/CTS | Request to Send / Clear to Send – handles hidden node problem |
| Roaming | Client moves between WAPs within the same network |
| BSS | Basic Service Set – single WAP + clients |
| ESS | Extended Service Set – multiple WAPs, same SSID |

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

## ✅ Study Checklist

- [ ] Explain the difference between static and dynamic routing
- [ ] Compare routing protocols (RIP, OSPF, EIGRP, BGP) by AD and metric
- [ ] Describe how PAT/NAT works
- [ ] Configure and verify VLANs on a switch
- [ ] Explain STP and RSTP port states
- [ ] Compare 802.11 wireless standards by band and speed
- [ ] Identify appropriate wireless security protocols
- [ ] Select correct cable type for a given scenario

---

## 🔗 Related Resources

- [CLI Commands](../Resources/cli-commands.md)
- [Labs – Routing & Switching](../Labs/README.md)
