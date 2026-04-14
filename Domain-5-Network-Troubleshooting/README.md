# Domain 5 – Network Troubleshooting (20%)

This domain tests your ability to diagnose and resolve network problems using a structured methodology and the appropriate tools. Expect approximately **20%** of exam questions from this domain.

---

## 📚 Key Topics

### 5.1 Troubleshooting Methodology

CompTIA defines a **7-step troubleshooting process** that you must know for the exam.

See the full detailed guide: **[troubleshooting-methodology.md](./troubleshooting-methodology.md)**

#### Quick Reference

| Step | Action |
|------|--------|
| 1 | Identify the problem |
| 2 | Establish a theory of probable cause |
| 3 | Test the theory to determine the cause |
| 4 | Establish a plan of action to resolve the problem |
| 5 | Implement the solution or escalate |
| 6 | Verify full system functionality |
| 7 | Document findings, actions, and outcomes |

---

### 5.2 Troubleshooting Tools

#### Command-Line Tools

| Tool | OS | Purpose |
|------|----|---------|
| `ping` | All | Tests ICMP reachability; checks latency |
| `traceroute` / `tracert` | Linux / Windows | Shows hop-by-hop path to destination |
| `ipconfig` | Windows | Shows IP configuration, default gateway, DNS |
| `ifconfig` / `ip a` | Linux | Shows IP configuration |
| `nslookup` | All | Queries DNS; resolves hostnames |
| `dig` | Linux/Mac | Advanced DNS queries |
| `netstat` | All | Shows active connections and listening ports |
| `ss` | Linux | Replacement for netstat; faster |
| `arp -a` | All | Displays ARP cache (IP-to-MAC mappings) |
| `route print` / `ip route` | Win / Linux | Displays routing table |
| `nmap` | All | Port scanner; network inventory |
| `tcpdump` | Linux/Mac | CLI packet capture |
| `pathping` | Windows | Combines ping + tracert with packet loss stats |
| `mtr` | Linux | Real-time traceroute with statistics |

> See [`/Resources/cli-commands.md`](../Resources/cli-commands.md) for full command syntax and examples.

#### Hardware Tools

| Tool | Purpose |
|------|---------|
| Cable Tester | Verifies cable continuity and wiring |
| Loopback Adapter | Tests NIC/port by looping signal back |
| Tone Generator / Probe | Traces cables through walls/ceilings |
| Optical Power Meter | Measures fiber signal strength |
| OTDR | Optical Time-Domain Reflectometer; finds fiber breaks |
| Multimeter | Tests voltage, continuity |
| Wi-Fi Analyzer | Identifies SSIDs, channels, signal strength |

#### Software Tools

| Tool | Purpose |
|------|---------|
| Wireshark | GUI packet capture and analysis |
| SolarWinds NPM | Network performance monitoring |
| Nagios / Zabbix | Open-source network monitoring |
| NetFlow Analyzer | Traffic flow analysis |
| iPerf | Measures network bandwidth between two points |

---

### 5.3 Common Connectivity Issues and Causes

| Symptom | Possible Cause(s) |
|---------|-------------------|
| Can't ping default gateway | Wrong IP/mask/gateway config; NIC down |
| Can resolve IP but not hostname | DNS misconfiguration or failure |
| Limited connectivity (APIPA 169.254.x.x) | DHCP failure |
| Slow network / high latency | Congestion, duplex mismatch, faulty cable |
| Intermittent connectivity | Loose cable, interference, STP topology change |
| No connectivity after VLAN change | Port not in correct VLAN; trunk misconfigured |
| Asymmetric routing | Multiple paths with inconsistent configurations |
| High packet loss on wireless | RF interference, distance, channel overlap |
| IP conflict | Two devices with same IP address |

---

### 5.4 Wireless Troubleshooting

| Issue | Likely Cause | Fix |
|-------|-------------|-----|
| Weak signal | Distance, obstacles | Move closer, add WAP |
| Interference | Channel overlap (2.4 GHz) | Change to channel 1, 6, or 11 |
| Can't associate | Wrong password / security mismatch | Verify WPA2/WPA3 settings |
| DHCP failure on wireless | WAP not bridging DHCP requests | Check DHCP forwarding / relay |
| Roaming issues | Sticky client; threshold too high | Adjust signal thresholds / 802.11r |

---

## ✅ Study Checklist

- [ ] Recite all 7 CompTIA troubleshooting steps in order
- [ ] Know when to use ping vs. traceroute vs. nslookup
- [ ] Identify what APIPA address indicates
- [ ] Explain the purpose of Wireshark vs. tcpdump
- [ ] Describe hardware tools and their uses (cable tester, OTDR, tone generator)
- [ ] Diagnose a scenario where a host has a 169.254.x.x address
- [ ] Identify common wireless issues and their solutions

---

## 🔗 Related Resources

- [Troubleshooting Methodology (7 Steps)](./troubleshooting-methodology.md)
- [CLI Commands](../Resources/cli-commands.md)
- [Labs](../Labs/README.md)
