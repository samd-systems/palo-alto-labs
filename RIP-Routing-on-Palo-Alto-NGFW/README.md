![Topology](topology.png)

![Validation](validation-1.png)

![Validation](validation-2.png)

# Lab – RIP Routing on Palo Alto NGFW

## Overview
This lab demonstrates RIP control-plane behavior between a Palo Alto Networks next-generation firewall and Cisco routing peers in a shared routing environment. The focus is on dynamic route exchange, adjacency formation, and next-hop resolution as observed on the firewall.

This lab is documented as a validated engineering case note rather than a configuration walkthrough.

## Lab Objectives
- Demonstrate successful RIP adjacency formation between the firewall and routing peers
- Confirm dynamic installation of RIP-learned routes on the firewall
- Demonstrate correct next-hop resolution for dynamically learned prefixes
- Observe stable routing behavior across the routing domain

## Topology Summary
The topology consists of Cisco routers and a Palo Alto Networks firewall exchanging RIP updates on a shared Layer-2 network segment. Loopback networks are advertised to demonstrate dynamic route propagation and next-hop selection.

## Configuration Summary
- RIP enabled on participating routing devices
- Loopback networks advertised dynamically
- Active and passive RIP interfaces defined

(Configuration details intentionally omitted; focus is on behavior and validation.)

## Validation and Results

### Proof of Operational State
- RIP adjacencies formed successfully between all participating devices
- Periodic RIP updates exchanged across the shared routing segment

### Route Installation and Resolution
- RIP-learned routes installed in the Palo Alto firewall routing table
- Correct next-hop resolution observed for all dynamically learned routes

### Stability
- Routing state remained stable throughout validation
- No unexpected adjacency flaps or route withdrawals observed

## Key Takeaways
- Palo Alto firewalls can participate reliably in legacy dynamic routing protocols
- Control-plane validation provides stronger assurance than configuration presence
- Observable routing outcomes confirm correct dynamic routing behavior

## Lab Environment
- Palo Alto Networks NGFW (VM-Series)
- Cisco IOS routers
- EVE-NG virtual lab platform

## Status
Validated and complete.
