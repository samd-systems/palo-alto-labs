![Topology](topology.png)

![Validation](validation-1.png)

![Validation](validation-2.png)

# Lab – Default Routing, Route Redistribution, and Inter-Zone Policy Enforcement

## Overview
This lab demonstrates how a Palo Alto Networks NGFW handles default routing and route redistribution while enforcing explicit inter-zone security policy across defined trust boundaries. The focus is on observable routing state and policy-governed traffic behavior rather than configuration mechanics. 

This lab is documented as a validated engineering case note rather than a configuration walkthrough.

## Lab Objectives
- Confirm installation and use of a default route on the NGFW
- Verify redistribution of routing information between OSPF and static routes
- Validate correct next-hop resolution for inside and outside networks
- Demonstrate that inter-zone traffic is permitted by security policy rather than routing state

## Topology Summary
The topology consists of multiple Cisco routers participating in OSPF within an Inside zone, a Palo Alto Networks NGFW acting as the routing and security boundary, and an Outside zone using default routing. The firewall separates trust zones and governs all traffic between them through explicit security policy.

## Configuration Summary
- Virtual router configuration supporting OSPF and static default routing
- Route redistribution between OSPF-learned networks and the default route
- Zone-based interface assignment for Inside and Outside segments
- Explicit inter-zone security policy permitting controlled traffic flow

(Configuration details intentionally omitted; focus is on behavior and validation.)

## Validation and Results

### Proof of Correct Operational State
- The NGFW routing table shows a valid default route pointing toward the Outside zone
- OSPF-learned routes from Inside zone routers are present and stable
- Connected and host routes are correctly installed on relevant interfaces
- Next-hop resolution aligns with expected zone boundaries

### Proof of Policy-Governed Traffic Behavior
- Bidirectional traffic between Inside and Outside networks was generated
- Traffic matched an explicit inter-zone security policy rule
- Security policy hit counts incremented, confirming active enforcement
- Traffic flow occurred only as a result of policy evaluation, not implicit routing behavior

This permissive inter-zone rule is intentionally used to demonstrate that routing enables reachability, but security policy—not routing—ultimately determines whether traffic is permitted.

## Key Takeaways
- Routing state enables reachability but does not grant permission
- Inter-zone communication is explicitly governed by security policy
- Policy hit counts provide defensible evidence of enforcement behavior

## Lab Environment
- Palo Alto Networks NGFW (VM-Series)
- Cisco routers
- EVE-NG virtual lab platform

## Status
Validated and complete.
