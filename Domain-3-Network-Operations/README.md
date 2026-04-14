# Domain 3 – Network Operations (17%)

This domain covers the operational management of a network, including monitoring, documentation, and ensuring business continuity. Expect approximately **17%** of exam questions from this domain.

---

## 📚 Key Topics

### 3.1 Network Monitoring and Management

#### SNMP (Simple Network Management Protocol)

| Version | Security | Notes |
|---------|----------|-------|
| SNMPv1 | Community strings (plaintext) | Legacy; avoid |
| SNMPv2c | Community strings (plaintext) | Adds bulk transfers |
| SNMPv3 | AuthPriv (auth + encryption) | Use in production |

- **Manager** – Polls or receives traps from agents (UDP 161 polls, UDP 162 traps)
- **Agent** – Runs on the monitored device
- **MIB** – Management Information Base; defines what can be monitored
- **OID** – Object Identifier; unique path to a value in the MIB

#### Syslog

| Severity | Level | Example |
|----------|-------|---------|
| Emergency | 0 | System unusable |
| Alert | 1 | Immediate action needed |
| Critical | 2 | Hardware failure |
| Error | 3 | Routing errors |
| Warning | 4 | Interface flapping |
| Notice | 5 | Normal but significant |
| Informational | 6 | Login events |
| Debug | 7 | Verbose diagnostic output |

- Default port: **UDP 514** (TCP 514 for reliable syslog per RFC 3195)
- Logs should be sent to a centralized **syslog server**.

#### Network Monitoring Protocols / Tools

| Tool / Protocol | Purpose |
|-----------------|---------|
| SNMP | Device health, interface stats, traps |
| Syslog | Event and error logging |
| NetFlow / IPFIX | Traffic flow analysis and bandwidth monitoring |
| RMON | Remote monitoring extension of SNMP |
| NTP (UDP 123) | Time synchronization (critical for log correlation) |

#### Bandwidth and Performance Metrics

| Metric | Description |
|--------|-------------|
| Bandwidth | Maximum theoretical throughput |
| Throughput | Actual data transferred |
| Latency | Time for a packet to travel source → destination |
| Jitter | Variation in latency (critical for VoIP) |
| Packet Loss | Percentage of packets that don't arrive |

---

### 3.2 Network Documentation

Good documentation is essential for troubleshooting and compliance.

#### Documentation Types

| Document | Description |
|----------|-------------|
| Network Diagram | Visual map of devices, links, and topologies |
| Physical Diagram | Physical locations of hardware and cabling |
| Logical Diagram | IP addressing, VLANs, routing paths |
| Rack Diagram | Equipment placement in server racks |
| IP Address Management (IPAM) | Tracks IP assignments across the network |
| Configuration Baseline | Standard device configuration |
| Change Log | Record of all network changes |
| SLA | Service Level Agreement – uptime/performance commitments |

#### Cable Management

- Label all cables and patch panel ports.
- Document patch panel to switch port mappings.
- Use color coding for different VLAN or link types.
- Maintain cable plant documentation (structured cabling).

---

### 3.3 Business Continuity and Disaster Recovery (BC/DR)

#### Key Concepts

| Term | Definition |
|------|-----------|
| RTO | Recovery Time Objective – max acceptable downtime |
| RPO | Recovery Point Objective – max acceptable data loss (time) |
| MTTR | Mean Time to Repair – average repair time |
| MTBF | Mean Time Between Failures – average time between outages |
| Fault Tolerance | System continues operating despite component failure |
| High Availability (HA) | Design for near-zero downtime (e.g., 99.999% = "five nines") |

#### Redundancy Strategies

| Strategy | Description |
|----------|-------------|
| Redundant Links | Multiple physical connections between devices |
| Redundant Power (UPS) | Uninterruptible Power Supply; protects against power failure |
| Redundant Hardware | Hot spare / failover device ready to take over |
| Load Balancing | Distributes traffic across multiple servers/links |
| Geographic Redundancy | Secondary site in different location |

#### Backup Types

| Type | What It Backs Up | Restore Speed | Storage |
|------|-----------------|---------------|---------|
| Full | Everything | Fastest | Most |
| Incremental | Changes since last backup | Slowest | Least |
| Differential | Changes since last full | Medium | Medium |

#### Site Types

| Site | Description | Cost |
|------|-------------|------|
| Hot Site | Fully operational duplicate; near-instant failover | Highest |
| Warm Site | Partially configured; needs some setup | Medium |
| Cold Site | Empty facility; must build out on failure | Lowest |

---

### 3.4 IP Management

#### DHCP Operation (DORA)

1. **Discover** – Client broadcasts to find DHCP server
2. **Offer** – Server offers an IP address
3. **Request** – Client requests the offered IP
4. **Acknowledge** – Server confirms the assignment

#### DHCP Lease Options

| Option | Description |
|--------|-------------|
| Lease Time | How long the IP is valid |
| Scope | Range of IPs available to lease |
| Exclusion | IPs within scope not available for leasing |
| Reservation | DHCP always assigns the same IP to a specific MAC |

#### DNS Record Types

| Record | Purpose |
|--------|---------|
| A | Maps hostname → IPv4 |
| AAAA | Maps hostname → IPv6 |
| CNAME | Alias; maps one hostname to another |
| MX | Mail exchanger; directs email |
| PTR | Reverse DNS; maps IP → hostname |
| NS | Name server; delegates DNS zone |
| TXT | Text records (SPF, DKIM, verification) |
| SOA | Start of Authority; zone metadata |

---

## ✅ Study Checklist

- [ ] Explain SNMP versions and when to use v3
- [ ] List syslog severity levels 0–7
- [ ] Calculate RTO, RPO, MTTR, and MTBF
- [ ] Compare full, incremental, and differential backups
- [ ] Compare hot, warm, and cold sites
- [ ] Describe DHCP DORA process
- [ ] Identify DNS record types and their purposes
- [ ] Explain NetFlow and its use in traffic analysis

---

## 🔗 Related Resources

- [CLI Commands](../Resources/cli-commands.md)
- [Labs](../Labs/README.md)
