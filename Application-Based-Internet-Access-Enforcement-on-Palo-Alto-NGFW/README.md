![Topology](topology.png)

![Validation](validation-1.png)

![Validation](validation-2.png)

# Lab – Application-Based Internet Access Enforcement on Palo Alto NGFW

## Overview
This lab validates application-based outbound Internet access by restricting a specific internal host to explicitly permitted application using Palo Alto NGFW App-ID with URL filtering.

While YouTube is used here as a representative application, the same enforcement model applies to any approved SaaS or web application.

The content is documented as a validated engineering case note rather than a configuration walkthrough.

## Lab Objectives
- Demonstrate baseline unrestricted outbound Internet behavior
- Confirm source NAT functionality for inside-to-outside traffic
- Enforce application-specific outbound access for a single internal host
- Verify application-level enforcement using firewall behavioral evidence

## Topology Summary
The topology consists of two internal hosts connected via a Layer 2 switch to a Palo Alto NGFW. The firewall separates an inside zone from an outside Internet-facing zone, with source NAT applied for outbound connectivity. A dedicated management interface is used for administrative access. One internal host is treated as a controlled participant subject to application restrictions.

## Configuration Summary
- Security zoning separating inside and outside trust boundaries
- Source NAT for outbound Internet access
- Baseline security policy permitting outbound connectivity
- Application-based security policy enforcing YouTube-only access
- URL filtering profile applied to constrain permitted destinations during application identification

(Configuration details intentionally omitted; focus is on behavior and validation.)

## Validation and Results

### Behavior Without the Control
Prior to application enforcement, the internal host generated multiple concurrent outbound sessions across different applications, including SSL and DNS. Traffic logs confirm unrestricted Internet access with successful NAT translation.

### Behavior With the Control
After enforcement, outbound traffic permitted from the host was identified as YouTube (youtube-base) by App-ID, with firewall traffic logs confirming application-aware policy enforcement and intended access constraints.

## Key Takeaways
- Application-aware controls provide precision beyond port-based filtering
- Source NAT enables outbound connectivity without exposing internal addressing
- Behavioral validation confirms effective enforcement of security intent

## Lab Environment
- Palo Alto NGFW
- Cisco Switch
- Client workstations
- EVE-NG lab environment

## Status
Validated and complete.
