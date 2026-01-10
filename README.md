# Palo Alto Next-Generation Firewall & Network Engineering Labs

This repository documents a curated set of hands-on engineering labs focused on practical firewall, routing, and network security design using Palo Alto Networks next-generation firewalls in multi-vendor environments.

Labs are executed and validated in an EVE-NG virtual lab environment to simulate real-world network topologies, routing domains, and security enforcement scenarios.

The emphasis is on non-trivial configurations, observable system behavior, and validation of outcomes rather than walkthrough-style or tutorial-based exercises.

---

## Capability Areas Demonstrated

The labs in this repository collectively demonstrate the following core network and security engineering capabilities:

### Routing & Control Plane Behavior
- Dynamic routing protocols (RIP, OSPF, BGP)
- Route propagation, authentication, and stability
- Default routing and route redistribution
- Deterministic path selection and failover behavior

### Network Segmentation & Zone Design
- Inter-zone traffic flows
- Inter-VLAN segmentation
- Trust boundary definition and enforcement
- Zone-based security posture

### Access Control & Policy Enforcement
- Explicit inter-zone security policy
- Least-privilege access design
- Policy-driven traffic enforcement independent of routing

### Application Awareness & Visibility
- Application identification using App-ID
- Application-based access control
- Enforcement based on observed application behavior rather than ports

### Threat Prevention & Inline Inspection
- SSL Forward Proxy inspection
- Threat Prevention enforcement on permitted traffic
- Vulnerability Protection applied inline
- DoS and Zone Protection mechanisms

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
