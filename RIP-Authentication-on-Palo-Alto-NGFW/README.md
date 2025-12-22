![Topology](topology.png)

![Validation](validation-1.png)

![Validation](validation-2.png)

# RIP Authentication on Palo Alto NGFW

## Overview
This lab validates the use of authentication in the RIP dynamic routing protocol to protect routing updates exchanged between a Palo Alto Networks firewall and Cisco routers. The focus is on preventing unauthorized route injection and confirming that only authenticated RIP updates are accepted within a shared routing domain.

This lab is documented as a validated engineering case note rather than a step-by-step configuration walkthrough.

---

## Lab Objectives
- Enable RIP authentication between a Palo Alto firewall and Cisco routers
- Establish secure RIP adjacencies using authenticated updates
- Validate routing behavior with authentication enabled
- Observe protocol behavior when unauthenticated updates are present

---

## Topology Summary
The topology consists of Cisco routers and a Palo Alto Networks firewall exchanging RIP updates on a shared broadcast network. An additional device on the same segment is used to demonstrate the risk of unauthenticated routing updates and to validate enforcement of RIP authentication.

---

## Configuration Summary
- RIP authentication enabled on the Palo Alto firewall
- Matching authentication configured on Cisco routers
- RIP updates restricted to authenticated peers
- Loopback networks advertised to validate authenticated route exchange

*(Detailed configuration steps are intentionally omitted to emphasize protocol behavior and validation outcomes.)*

---

## Validation and Results
- RIP updates without authentication were observable on the network prior to enforcement
- After enabling authentication, RIP updates included authentication information
- Only authenticated RIP responses were accepted by participating devices
- Unauthorized or unauthenticated routing updates were effectively rejected

---

## Key Takeaways
- Dynamic routing protocols require authentication to prevent route injection
- Palo Alto firewalls support authenticated RIP exchanges in multi-vendor environments
- Packet-level inspection is an effective method for validating routing security controls
- Security validation should confirm both acceptance of valid updates and rejection of invalid ones

---

## Lab Environment
- Palo Alto Networks NGFW (VM-Series)
- Cisco IOS routers
- EVE-NG virtual lab platform
- Wireshark (packet capture and protocol analysis)

---

### ✅ Status
Validated and complete.
