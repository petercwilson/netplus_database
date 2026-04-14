# IPv4 Subnetting Cheat Sheet

A complete reference for CompTIA Network+ N10-009 subnetting questions.

---

## The Magic Formula

```
Usable Hosts = 2^(host bits) - 2
Subnets      = 2^(borrowed bits)
```

- Subtract 2 from hosts because: **network address** + **broadcast address** are unusable.
- Host bits = 32 − prefix length

---

## Complete CIDR Reference Table

| CIDR | Subnet Mask | Wildcard Mask | # Hosts | # Usable Hosts | Block Size |
|------|-------------|---------------|---------|----------------|------------|
| /32 | 255.255.255.255 | 0.0.0.0 | 1 | 0 (host route) | 1 |
| /31 | 255.255.255.254 | 0.0.0.1 | 2 | 2 (point-to-point) | 2 |
| /30 | 255.255.255.252 | 0.0.0.3 | 4 | 2 | 4 |
| /29 | 255.255.255.248 | 0.0.0.7 | 8 | 6 | 8 |
| /28 | 255.255.255.240 | 0.0.0.15 | 16 | 14 | 16 |
| /27 | 255.255.255.224 | 0.0.0.31 | 32 | 30 | 32 |
| /26 | 255.255.255.192 | 0.0.0.63 | 64 | 62 | 64 |
| /25 | 255.255.255.128 | 0.0.0.127 | 128 | 126 | 128 |
| /24 | 255.255.255.0 | 0.0.0.255 | 256 | 254 | 256 |
| /23 | 255.255.254.0 | 0.0.1.255 | 512 | 510 | 512 |
| /22 | 255.255.252.0 | 0.0.3.255 | 1,024 | 1,022 | 1,024 |
| /21 | 255.255.248.0 | 0.0.7.255 | 2,048 | 2,046 | 2,048 |
| /20 | 255.255.240.0 | 0.0.15.255 | 4,096 | 4,094 | 4,096 |
| /19 | 255.255.224.0 | 0.0.31.255 | 8,192 | 8,190 | 8,192 |
| /18 | 255.255.192.0 | 0.0.63.255 | 16,384 | 16,382 | 16,384 |
| /17 | 255.255.128.0 | 0.0.127.255 | 32,768 | 32,766 | 32,768 |
| /16 | 255.255.0.0 | 0.0.255.255 | 65,536 | 65,534 | 65,536 |
| /15 | 255.254.0.0 | 0.1.255.255 | 131,072 | 131,070 | 131,072 |
| /14 | 255.252.0.0 | 0.3.255.255 | 262,144 | 262,142 | 262,144 |
| /13 | 255.248.0.0 | 0.7.255.255 | 524,288 | 524,286 | 524,288 |
| /12 | 255.240.0.0 | 0.15.255.255 | 1,048,576 | 1,048,574 | 1,048,576 |
| /11 | 255.224.0.0 | 0.31.255.255 | 2,097,152 | 2,097,150 | 2,097,152 |
| /10 | 255.192.0.0 | 0.63.255.255 | 4,194,304 | 4,194,302 | 4,194,304 |
| /9 | 255.128.0.0 | 0.127.255.255 | 8,388,608 | 8,388,606 | 8,388,608 |
| /8 | 255.0.0.0 | 0.255.255.255 | 16,777,216 | 16,777,214 | 16,777,216 |

---

## Octet Value Reference

When the subnet boundary falls within an octet, use this table to find the block size and range:

| Prefix Bits in Octet | Subnet Mask Value | Block Size |
|---------------------|-------------------|------------|
| /25 → 1 bit | 128 | 128 |
| /26 → 2 bits | 192 | 64 |
| /27 → 3 bits | 224 | 32 |
| /28 → 4 bits | 240 | 16 |
| /29 → 5 bits | 248 | 8 |
| /30 → 6 bits | 252 | 4 |
| /31 → 7 bits | 254 | 2 |
| /32 → 8 bits | 255 | 1 |

> **Tip:** Block size = 256 − subnet mask octet value. E.g., 256 − 240 = 16 (block size for /28).

---

## Subnetting Step-by-Step Example

**Problem:** You have 192.168.10.0/24 and need to subnet it into /27 subnets. List the first three subnets.

**Step 1 – Find block size:**
- /27 → subnet mask = 255.255.255.224
- Block size = 256 − 224 = **32**

**Step 2 – List subnets (increment by block size):**

| Subnet | Network Address | Usable Range | Broadcast |
|--------|----------------|-------------|-----------|
| 1st | 192.168.10.0 | .1 – .30 | .31 |
| 2nd | 192.168.10.32 | .33 – .62 | .63 |
| 3rd | 192.168.10.64 | .65 – .94 | .95 |
| 4th | 192.168.10.96 | .97 – .126 | .127 |
| ... | ... | ... | ... |
| 8th | 192.168.10.224 | .225 – .254 | .255 |

---

## VLSM (Variable Length Subnet Masking) Quick Process

1. **Sort** your required subnets from **largest to smallest**.
2. Assign the **smallest subnet mask** that fits each requirement.
3. Work through the address space sequentially, without overlap.

**Example:** Allocate from 10.0.0.0/24:
- Dept A needs 100 hosts → /25 (126 usable) → 10.0.0.0/25 (.1–.126)
- Dept B needs 50 hosts → /26 (62 usable) → 10.0.0.128/26 (.129–.190)
- Dept C needs 20 hosts → /27 (30 usable) → 10.0.0.192/27 (.193–.222)
- WAN Link → /30 (2 usable) → 10.0.0.224/30 (.225–.226)

---

## Private Address Ranges (RFC 1918)

| Range | CIDR | Class | Total Hosts |
|-------|------|-------|-------------|
| 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 | A | ~16.7 million |
| 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 | B | ~1 million |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 | C | ~65,536 |

---

## Special Addresses

| Address | Purpose |
|---------|---------|
| 0.0.0.0/0 | Default route (all traffic) |
| 127.0.0.0/8 | Loopback range |
| 127.0.0.1 | Localhost |
| 169.254.0.0/16 | APIPA (link-local auto-assigned) |
| 255.255.255.255 | Limited broadcast (all hosts on local subnet) |

---

## Exam Tips

- **Memorize the /24–/30 range** — most exam questions use these.
- **Block size trick:** 256 − last non-255 octet = block size.
- **Host check:** If given an IP and mask, find which subnet it belongs to by dividing the host octet by the block size.
  - Example: 192.168.1.77 /27 → block = 32 → 77 ÷ 32 = 2 remainder 13 → subnet = 192.168.1.64, broadcast = .95
- **Point-to-point links** always use /30 (2 usable hosts).
- **/31** is valid for point-to-point links per RFC 3021 (no broadcast needed).
