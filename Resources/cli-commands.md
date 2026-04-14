# CLI Commands – Network Diagnostic & Configuration Cheat Sheet

Essential command-line tools and syntax for CompTIA Network+ N10-009.

---

## Diagnostic Commands

### `ping` – Test ICMP Reachability

```bash
# Basic ping (Linux/Mac)
ping 8.8.8.8

# Ping with count (Linux)
ping -c 4 8.8.8.8

# Ping with count (Windows)
ping -n 4 8.8.8.8

# Ping loopback (test TCP/IP stack)
ping 127.0.0.1

# Ping with specific size (Windows)
ping -l 1472 8.8.8.8
```

**Interpreting results:**
- TTL expired → routing loop or too many hops
- Request timed out → host unreachable, firewall blocking ICMP, or offline
- Destination unreachable → routing problem

---

### `traceroute` / `tracert` – Path Discovery

```bash
# Linux/Mac
traceroute 8.8.8.8

# Windows
tracert 8.8.8.8

# Disable DNS resolution (faster, Linux)
traceroute -n 8.8.8.8

# Disable DNS resolution (faster, Windows)
tracert -d 8.8.8.8
```

**Interpreting results:**
- `* * *` → hop is not responding to ICMP (may be filtered, not necessarily broken)
- High RTT at a specific hop → latency introduced at that router
- Path ends before destination → destination unreachable

---

### `pathping` – Combined Ping + Traceroute (Windows)

```cmd
pathping 8.8.8.8
```

Shows per-hop latency and packet loss statistics over time.

---

### `mtr` – Real-Time Traceroute (Linux)

```bash
mtr 8.8.8.8
mtr --no-dns 8.8.8.8
```

Continuously updates per-hop statistics including loss%, avg latency.

---

### `nslookup` – DNS Query Tool

```bash
# Basic forward lookup
nslookup example.com

# Specify DNS server
nslookup example.com 8.8.8.8

# Reverse lookup (PTR record)
nslookup 93.184.216.34

# Query specific record type
nslookup -type=MX example.com
nslookup -type=NS example.com
nslookup -type=TXT example.com
```

---

### `dig` – Advanced DNS Queries (Linux/Mac)

```bash
# Basic query
dig example.com

# Query specific type
dig example.com MX
dig example.com NS
dig example.com AAAA

# Short output
dig +short example.com

# Query specific server
dig @8.8.8.8 example.com

# Reverse lookup
dig -x 93.184.216.34
```

---

### `ipconfig` – Windows IP Configuration

```cmd
# Show IP configuration
ipconfig

# Show full details (MAC, DHCP, DNS)
ipconfig /all

# Release DHCP lease
ipconfig /release

# Renew DHCP lease
ipconfig /renew

# Flush DNS cache
ipconfig /flushdns

# Display DNS cache
ipconfig /displaydns
```

---

### `ifconfig` – Linux/Mac IP Configuration (legacy)

```bash
# Show all interfaces
ifconfig

# Show specific interface
ifconfig eth0

# Bring interface up/down
ifconfig eth0 up
ifconfig eth0 down
```

---

### `ip` – Modern Linux Network Configuration

```bash
# Show all IP addresses
ip addr show
ip a

# Show specific interface
ip addr show eth0

# Show routing table
ip route show
ip r

# Add static route
ip route add 10.0.0.0/8 via 192.168.1.1

# Delete route
ip route del 10.0.0.0/8

# Show ARP table
ip neigh show

# Bring interface up/down
ip link set eth0 up
ip link set eth0 down
```

---

### `arp` – View/Manage ARP Cache

```bash
# Display ARP table (Linux/Windows)
arp -a

# Delete specific ARP entry (Windows)
arp -d 192.168.1.1

# Add static ARP entry (Windows)
arp -s 192.168.1.1 00-11-22-33-44-55
```

---

### `netstat` – Network Connections and Statistics

```bash
# Show all active connections
netstat -a

# Show listening ports only
netstat -l         # Linux
netstat -an        # Windows

# Show with process IDs (Linux)
netstat -tulnp

# Show routing table
netstat -r

# Show interface statistics
netstat -i         # Linux
netstat -e         # Windows
```

**Common flags (Linux):**
| Flag | Meaning |
|------|---------|
| -t | TCP connections |
| -u | UDP connections |
| -l | Listening only |
| -n | Show IPs (no DNS) |
| -p | Show process name/PID |

---

### `ss` – Socket Statistics (Linux replacement for netstat)

```bash
# Show all TCP connections
ss -t

# Show listening ports
ss -tlnp

# Show UDP
ss -u

# Show summary
ss -s
```

---

### `route` – Routing Table Management

```cmd
# Windows – display routing table
route print

# Windows – add route
route add 10.0.0.0 mask 255.0.0.0 192.168.1.1

# Windows – delete route
route delete 10.0.0.0

# Windows – add persistent route
route -p add 10.0.0.0 mask 255.0.0.0 192.168.1.1
```

```bash
# Linux – display routing table
route -n

# Linux (modern)
ip route show
```

---

## Cisco IOS Configuration Commands

### Basic Device Setup

```cisco
! Enter privileged mode
enable

! Enter global configuration mode
configure terminal

! Set hostname
hostname SW1

! Set enable secret
enable secret Str0ngP@ss

! Disable DNS lookup (stops IOS from resolving typos)
no ip domain-lookup

! Save configuration
copy running-config startup-config
! or
write memory
```

---

### Interface Configuration

```cisco
! Configure interface
interface GigabitEthernet0/1
 description Link-to-Router
 ip address 192.168.1.1 255.255.255.0
 no shutdown

! Show interface status
show interfaces GigabitEthernet0/1
show ip interface brief
```

---

### VLAN Configuration (Switch)

```cisco
! Create VLAN
vlan 10
 name Sales

! Assign port to VLAN (access)
interface FastEthernet0/1
 switchport mode access
 switchport access vlan 10

! Configure trunk port
interface GigabitEthernet0/1
 switchport mode trunk
 switchport trunk native vlan 999

! Verify VLANs
show vlan brief
show interfaces trunk
```

---

### Routing Configuration

```cisco
! Static route
ip route 10.0.0.0 255.0.0.0 192.168.1.2

! Default route
ip route 0.0.0.0 0.0.0.0 203.0.113.1

! Enable OSPF
router ospf 1
 network 192.168.1.0 0.0.0.255 area 0
 network 10.0.0.0 0.255.255.255 area 0

! Verify routing table
show ip route
```

---

### SSH Configuration (Cisco)

```cisco
! Set domain name (required for SSH key generation)
ip domain-name example.com

! Generate RSA keys (use 2048 bits minimum)
crypto key generate rsa modulus 2048

! Enable SSH v2
ip ssh version 2

! Configure VTY lines for SSH only
line vty 0 4
 transport input ssh
 login local

! Create local user
username admin privilege 15 secret Str0ngP@ss
```

---

### Port Security (Switch)

```cisco
interface FastEthernet0/1
 switchport mode access
 switchport port-security
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown

! Verify
show port-security interface FastEthernet0/1
```

---

### DHCP (Cisco Router as DHCP Server)

```cisco
! Exclude addresses from pool
ip dhcp excluded-address 192.168.1.1 192.168.1.10

! Create DHCP pool
ip dhcp pool LAN
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 8.8.8.8
 lease 7

! Verify
show ip dhcp binding
show ip dhcp pool
```

---

### ACL (Access Control List)

```cisco
! Standard ACL (matches source IP only)
access-list 10 permit 192.168.1.0 0.0.0.255
access-list 10 deny any

! Extended ACL
access-list 100 permit tcp 192.168.1.0 0.0.0.255 any eq 80
access-list 100 permit tcp 192.168.1.0 0.0.0.255 any eq 443
access-list 100 deny ip any any

! Apply ACL to interface
interface GigabitEthernet0/0
 ip access-group 100 in

! Verify
show access-lists
show ip interface GigabitEthernet0/0
```

---

### Useful Show Commands (Cisco)

| Command | Purpose |
|---------|---------|
| `show version` | IOS version, uptime, hardware |
| `show running-config` | Current running configuration |
| `show startup-config` | Saved configuration |
| `show ip route` | Routing table |
| `show ip interface brief` | Interface IPs and status |
| `show interfaces` | Detailed interface statistics |
| `show vlan brief` | VLAN assignments |
| `show interfaces trunk` | Trunk port information |
| `show mac address-table` | MAC address table |
| `show arp` | ARP table |
| `show ip dhcp binding` | DHCP leases |
| `show port-security` | Port security status |
| `show cdp neighbors` | Directly connected Cisco devices |
| `show spanning-tree` | STP topology |
| `show logging` | System log buffer |
| `show users` | Connected VTY sessions |
| `debug ip icmp` | Real-time ICMP debug (use carefully!) |
