# Palo Alto Next-Generation Firewall & Network Engineering Labs

This repository documents a curated set of hands-on engineering labs focused on practical firewall, routing, and network security design using Palo Alto Networks next-generation firewalls in multi-vendor environments.

Labs are executed and validated in an EVE-NG virtual lab environment to simulate real-world network topologies, routing domains, and security enforcement scenarios.

The emphasis is on non-trivial configurations, observable system behavior, and validation of outcomes rather than walkthrough-style or tutorial-based exercises.

---

## Capability Areas Demonstrated

The labs in this repository collectively demonstrate the following core network and security engineering capabilities:

### Routing & Control Plane Behavior
- Dynamic routing protocols (RIP, OSPF, BGP)
- Control-plane adjacency formation and route propagation
- Route authentication and routing stability
- Default routing and route redistribution
- Policy-based traffic steering and deterministic path selection

### Network Segmentation & Zone Design
- Zone-based security architecture and trust boundary definition
- Inter-zone traffic flow design
- Inter-VLAN segmentation and isolation
- Segmentation enforcement independent of routing state

### Access Control & Policy Enforcement
- Explicit inter-zone security policy enforcement
- Least-privilege access design across security zones
- Policy-driven traffic enforcement independent of routing decisions
- Security policy evaluation relative to NAT translation

### Application Awareness & Visibility
- Application identification using App-ID
- Dynamic application classification and reclassification
- Application-based access control enforcement
- Enforcement based on application behavior rather than ports

### Identity-Based Access Control
- User-to-IP mapping using User-ID
- Captive Portal–based user identification
- Identity-aware policy enforcement across security zones
- Integration of user context into access control decisions

### Secure Connectivity & VPN
- Site-to-site IPsec VPN design and tunnel-based routing
- Secure inter-site communication over untrusted networks
- Remote access VPN using GlobalProtect
- Zone-based policy enforcement for VPN users

### Traffic Translation & Threat Prevention
- Source and destination NAT behavior and order of operations
- SSL Forward Proxy inspection and decrypted traffic enforcement
- Threat Prevention enforcement on permitted traffic
- Inline Vulnerability Protection enforcement
- Zone Protection and DoS mitigation mechanisms

---

## Labs

Each lab is documented as a validated engineering case note with supporting topology diagrams and validation artifacts.

- [Lab – RIP Routing on Palo Alto NGFW](RIP-Routing-on-Palo-Alto-NGFW/)
- [Lab – RIP Authentication on Palo Alto NGFW](RIP-Authentication-on-Palo-Alto-NGFW/)
- [Lab – OSPF Configuration on Palo Alto NGFW](OSPF-Configuration-on-Palo-Alto-NGFW/)
- [Lab – BGP Routing on Palo Alto NGFW](BGP-Routing-on-Palo-Alto-NGFW/)
- [Lab – Default Routing, Route Redistribution, and Inter-Zone Policy Enforcement on Palo Alto NGFW](Default-Routing-Route-Redistribution-and-Inter-Zone-Policy-on-Palo-Alto-NGFW/)
- [Lab – Application-Based Internet Access Enforcement on Palo Alto NGFW](Application-Based-Internet-Access-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – SSL Forward Proxy on Palo Alto NGFW](SSL-Forward-Proxy-on-Palo-Alto-NGFW/)
- [Lab – Threat Prevention Enforcement on Palo Alto NGFW](Threat-Prevention-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – Vulnerability Protection Enforcement on Palo Alto NGFW](Vulnerability-Protection-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – Zone and DoS Protection on Palo Alto NGFW](Zone-and-DoS-Protection-on-Palo-Alto-NGFW/)
- [Lab – Inter-VLAN Segmentation on Palo Alto NGFW](Inter-VLAN-Segmentation-on-Palo-Alto-NGFW/)
- [Lab – Captive Portal User-ID Enforcement on Palo Alto NGFW](Captive-Portal-User-ID-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – Policy-Based Forwarding Path Override on Palo Alto NGFW](Policy-Based-Forwarding-Path-Override-on-Palo-Alto-NGFW/)
- [Lab – Destination NAT with Pre-NAT Security Policy Matching on Palo Alto NGFW](Destination-NAT-with-Pre-NAT-Security-Policy-Matching-on-Palo-Alto-NGFW/)
- [Lab – Site-to-Site IPsec VPN on Palo Alto NGFW](Site-to-Site-IPsec-VPN-on-Palo-Alto-NGFW/)
- [Lab – GlobalProtect Remote Access with Zone-Based Policy Enforcement on Palo Alto NGFW](GlobalProtect-Remote-Access-with-Zone-Based-Policy-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – Active/Passive HA Failover on Palo Alto NGFW](Active-Passive-HA-Failover-on-Palo-Alto-NGFW/)
- [Lab – External Syslog Forwarding on Palo Alto NGFW](External-Syslog-Forwarding-on-Palo-Alto-NGFW/)
