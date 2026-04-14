# CompTIA Network+ Troubleshooting Methodology

> **Domain 5 Reference** | CompTIA Network+ N10-009

CompTIA defines a formal **7-step troubleshooting methodology** that appears consistently on the exam. Internalizing these steps — and knowing *why* each step exists — will help you both pass the exam and resolve real-world network issues more efficiently.

---

## The 7-Step Troubleshooting Process

```
┌─────────────────────────────────────────────────────┐
│  1. Identify the Problem                            │
│  2. Establish a Theory of Probable Cause            │
│  3. Test the Theory to Determine the Cause          │
│  4. Establish a Plan of Action                      │
│  5. Implement the Solution or Escalate              │
│  6. Verify Full System Functionality                │
│  7. Document Findings, Actions, and Outcomes        │
└─────────────────────────────────────────────────────┘
```

---

## Step 1 – Identify the Problem

**Goal:** Gather as much information as possible before attempting a fix.

### Actions

- **Question the user(s)** affected by the problem.
- **Identify symptoms** – What exactly is failing? What is still working?
- **Gather information** from logs, monitoring tools, and error messages.
- **Determine if anything changed** recently (new hardware, software update, configuration change).
- **Duplicate the problem** if possible to confirm it is reproducible.

### Key Questions to Ask

| Question | Why It Matters |
|----------|---------------|
| When did the problem start? | Helps correlate with recent changes |
| Has anything changed recently? | Most outages follow a change event |
| Who and what is affected? | Scopes the problem (one user vs. all users) |
| Is the problem intermittent or constant? | Intermittent issues are harder to diagnose |
| What error messages appear? | Often point directly to the cause |

### Tools to Use

- Ping, traceroute, nslookup for initial connectivity checks
- Review system and network logs (syslog, event viewer)
- Check network monitoring dashboards (SNMP, NetFlow)

> **Exam Tip:** On the exam, "identify the problem" always comes before forming any theory. Never skip straight to a fix.

---

## Step 2 – Establish a Theory of Probable Cause

**Goal:** Form one or more hypotheses about what *could* be causing the problem.

### Actions

- Based on symptoms gathered in Step 1, list possible causes.
- Consider the **OSI model** as a structured framework — start at Layer 1 (physical) and work up, or start at the most likely layer based on symptoms.
- Think about **what changed** and whether it could be the cause.
- Consider multiple theories and rank them from most to least likely.

### OSI-Layered Approach

| OSI Layer | Common Issues to Consider |
|-----------|--------------------------|
| Layer 1 – Physical | Bad cable, unplugged NIC, fiber break, wrong port |
| Layer 2 – Data Link | Wrong VLAN, duplex mismatch, MAC table issue, STP loop |
| Layer 3 – Network | Wrong IP/mask/gateway, routing issue, NAT failure |
| Layer 4 – Transport | Firewall blocking port, wrong port, session table full |
| Layer 5–7 – Upper | DNS failure, application crash, authentication error |

> **Exam Tip:** CompTIA often expects you to approach from the bottom of the OSI model upward. Start physical, then logical.

---

## Step 3 – Test the Theory to Determine the Cause

**Goal:** Confirm (or eliminate) each theory without making permanent changes yet.

### Actions

- Test the **simplest and most likely** theory first.
- Use non-destructive tests where possible (e.g., run a ping test before changing configuration).
- If the theory is **confirmed** → move to Step 4.
- If the theory is **not confirmed** → discard it and return to Step 2 to form a new theory.
- If you **cannot test** the theory yourself (e.g., ISP issue), escalate.

### Common Testing Techniques

| Test | What It Confirms |
|------|-----------------|
| Ping loopback (127.0.0.1) | TCP/IP stack is functional |
| Ping default gateway | Local network connectivity is functional |
| Ping remote IP | Routing is functional |
| nslookup / dig | DNS resolution is functional |
| traceroute / tracert | Shows where the path breaks |
| Check link lights | Physical layer connectivity |
| Swap cable or port | Isolates physical component failure |
| Check VLAN assignment | Layer 2 configuration |

> **Exam Tip:** Testing the theory does NOT mean applying the fix yet. Confirm the root cause first.

---

## Step 4 – Establish a Plan of Action to Resolve the Problem and Identify Potential Effects

**Goal:** Create a structured, safe plan to fix the problem before touching production systems.

### Actions

- Define the **specific steps** needed to resolve the confirmed cause.
- Identify **potential side effects** or risks of the proposed fix.
  - Example: Changing a VLAN may affect other devices on the port.
  - Example: Restarting a core switch will drop all connected clients.
- Check the **change management process** — does this require a change request or approval?
- Plan for **rollback** — how will you reverse the change if it makes things worse?
- Schedule maintenance windows if the fix will cause downtime.

### Plan of Action Template

```
Problem:      [Brief description of confirmed root cause]
Fix:          [Step-by-step resolution actions]
Side Effects: [What else might be impacted]
Rollback:     [How to reverse if needed]
Approval:     [Change management ticket number, if required]
Window:       [When the fix will be applied]
```

> **Exam Tip:** The plan of action step explicitly includes identifying *potential effects* — this is important for exam questions about change management and risk.

---

## Step 5 – Implement the Solution or Escalate as Necessary

**Goal:** Execute the plan to resolve the problem.

### Actions

- Follow the plan created in Step 4 precisely.
- Make **one change at a time** where possible to isolate effects.
- Monitor the network during and immediately after the change.
- If the fix is beyond your skill level, tools, or access: **escalate** to senior staff, vendor support, or the ISP.

### When to Escalate

| Situation | Escalation Path |
|-----------|-----------------|
| Outside your scope of authority | Senior engineer / manager |
| Requires vendor-specific tools | Vendor TAC (Technical Assistance Center) |
| ISP circuit issue | ISP NOC (Network Operations Center) |
| Security incident | Security team / SOC |
| Hardware failure under warranty | Vendor RMA process |

> **Exam Tip:** Escalation is a valid and professional option — the exam may test whether you know *when* to escalate rather than attempt a fix outside your authority.

---

## Step 6 – Verify Full System Functionality and Implement Preventative Measures

**Goal:** Confirm the problem is fully resolved and prevent it from recurring.

### Actions

- **Test the original symptom** – is it gone?
- **Test adjacent systems** – did your fix accidentally break something else?
- **Verify from the user's perspective** – have the affected user(s) confirm the issue is resolved.
- **Implement preventative measures** where applicable:
  - Update firmware / patches
  - Adjust monitoring thresholds
  - Add redundancy
  - Review and harden configurations

### Verification Checklist

- [ ] Original symptom is no longer present
- [ ] All affected users confirm resolution
- [ ] Adjacent/related systems are functioning normally
- [ ] No new alerts generated by the change
- [ ] Preventative measure implemented (if applicable)

> **Exam Tip:** This step includes *preventative measures* — don't forget that part of the step.

---

## Step 7 – Document Findings, Actions, and Outcomes

**Goal:** Create a clear record of the incident and resolution for future reference.

### Actions

- Record the **problem description** and its impact.
- Document the **root cause** identified.
- List all **steps taken** during troubleshooting and resolution.
- Note the **solution** that resolved the problem.
- Document **preventative measures** implemented.
- Update relevant documentation (network diagrams, IP address records, change logs).
- Close the support ticket and notify stakeholders.

### Documentation Template

```
Incident ID:       [Ticket / Change number]
Date/Time:         [When problem occurred and was resolved]
Reported By:       [User or monitoring system]
Affected Systems:  [Devices, services, or users impacted]
Symptoms:          [What was observed]
Root Cause:        [Confirmed cause of the problem]
Resolution:        [Steps taken to fix the problem]
Preventative:      [Action taken to prevent recurrence]
Resolved By:       [Technician name]
Time to Resolve:   [Duration of the incident]
```

> **Exam Tip:** Documentation is always the *last* step. Never document before the problem is fully verified as resolved.

---

## Summary: The 7 Steps at a Glance

| Step | Name | Key Verb |
|------|------|---------|
| 1 | Identify the Problem | **Gather** |
| 2 | Establish a Theory | **Hypothesize** |
| 3 | Test the Theory | **Confirm** |
| 4 | Establish a Plan of Action | **Plan** |
| 5 | Implement the Solution or Escalate | **Fix / Escalate** |
| 6 | Verify Full Functionality | **Validate** |
| 7 | Document | **Record** |

---

## Common Exam Scenarios

### Scenario 1: User cannot access the internet

```
Step 1: User reports "no internet." Can they ping the gateway? Reach internal resources?
Step 2: Theory – DHCP failure, gateway down, DNS failure, firewall rule
Step 3: ping 127.0.0.1 ✓ → ping gateway ✗ → Layer 3 issue confirmed
Step 4: Plan to check routing table, gateway reachability
Step 5: Fix gateway configuration (wrong IP on interface)
Step 6: User confirms internet access restored; check other users on same segment
Step 7: Document root cause (misconfigured gateway IP after firmware update)
```

### Scenario 2: Intermittent network drops on a specific switch port

```
Step 1: One workstation drops connection every few hours
Step 2: Theory – bad cable, duplex mismatch, STP topology change, NIC issue
Step 3: Check interface error counters → CRC errors found → physical layer issue
Step 4: Plan to replace patch cable between workstation and switch
Step 5: Replace cable; monitor port for 24 hours
Step 6: No further CRC errors; user confirms stable connection
Step 7: Document: faulty Cat5e patch cable replaced with Cat6
```

---

## Related Resources

- [Domain 5 README](./README.md)
- [CLI Commands Cheat Sheet](../Resources/cli-commands.md)
- [Common Ports Reference](../Resources/common-ports.md)
- [Labs – Troubleshooting Scenarios](../Labs/README.md)
