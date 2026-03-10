# Palo Alto Next-Generation Firewall & Network Engineering Labs

This repository documents a curated set of hands-on engineering labs and structured incident case studies focused on firewall architecture, dynamic routing behavior, segmentation design, and policy-driven security enforcement using Palo Alto Networks next-generation firewalls in multi-vendor environments.

The body of work demonstrates NGFW engineering capability across routing, segmentation, identity integration, and failure-state analysis through controlled, scenario-based validation. All scenarios are executed within an EVE-NG virtual lab environment modeled on production-style topologies and operational change conditions, including enforcement drift detection and failure-state recovery.

---

## Capability Areas Demonstrated

The labs and incident case studies in this repository collectively demonstrate the following core network and security engineering capabilities:

### Routing & Control Plane Behavior
- Dynamic routing protocols (RIP, OSPF, BGP)
- Control-plane adjacency formation and route propagation
- Route authentication and routing stability
- Default routing and route redistribution
- Policy-based traffic steering and deterministic path selection
- Troubleshooting routing misconfigurations and traffic blackholes

### Network Segmentation & Zone Design
- Zone-based security architecture and trust boundary definition
- Inter-zone traffic flow design
- Inter-VLAN segmentation and isolation
- Segmentation enforcement independent of routing state
- Validation of segmentation failures and policy conflicts

### Access Control & Policy Enforcement
- Explicit inter-zone security policy enforcement
- Least-privilege access design across security zones
- Policy-driven traffic enforcement independent of routing decisions
- Security policy evaluation relative to NAT translation
- Rule order evaluation and implicit deny analysis

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
- Troubleshooting encrypted traffic enforcement behavior

### High Availability & Resilience
- Active/Passive high availability architecture
- Stateful failover behavior and session continuity
- Redundancy design for firewall availability
- Validation of failover behavior under active traffic conditions

### Traffic Translation, Logging & Threat Prevention
- Source and destination NAT behavior and order of operations
- SSL Forward Proxy inspection and decrypted traffic enforcement
- Threat Prevention enforcement on permitted traffic
- Inline Vulnerability Protection enforcement
- Zone Protection and DoS mitigation mechanisms
- External syslog forwarding for centralized logging and visibility
- Log-driven investigation and traffic flow validation

---

## Repository Structure

This repository is organized into two primary categories:

Configuration & Design Labs  
Focused on feature implementation, behavioral validation, enforcement logic, and deterministic traffic design.

Incident Case Studies  
Focused on failure-state conditions, investigative workflow, root cause determination, corrective remediation, and post-fix validation artifacts.

---

## Incident Case Studies

Each incident is documented as a structured engineering case note including: observable symptoms, investigation methodology, root cause isolation, corrective action, and post-remediation validation.

- [Incident – Security Zone Misconfiguration on Palo Alto NGFW](Incident-Security-Zone-Misconfiguration-on-Palo-Alto-NGFW/)
- [Incident – Source NAT Conflict on Palo Alto NGFW](Incident-Source-NAT-Conflict-on-Palo-Alto-NGFW/)
- [Incident – IPsec Tunnel Selective Failure on Palo Alto NGFW](Incident-IPsec-Tunnel-Selective-Failure-on-Palo-Alto-NGFW/)
- [Incident – BGP Return Path Blackhole on Palo Alto NGFW](Incident-BGP-Return-Path-Blackhole-on-Palo-Alto-NGFW/)
- [Incident – SSL Forward Proxy Scope Failure on Palo Alto NGFW](Incident-SSL-Forward-Proxy-Scope-Failure-on-Palo-Alto-NGFW/)


This series will expand as additional incident scenarios are validated and documented.

---

## Configuration & Design Labs

Each lab is documented as a validated engineering case note with supporting topology diagrams and enforcement validation artifacts.

- [Lab – RIP Routing on Palo Alto NGFW](RIP-Routing-on-Palo-Alto-NGFW/)
- [Lab – RIP Authentication on Palo Alto NGFW](RIP-Authentication-on-Palo-Alto-NGFW/)
- [Lab – OSPF Configuration on Palo Alto NGFW](OSPF-Configuration-on-Palo-Alto-NGFW/)
- [Lab – BGP Routing on Palo Alto NGFW](BGP-Routing-on-Palo-Alto-NGFW/)
- [Lab – Inter-Zone Policy Enforcement on Palo Alto NGFW](Inter-Zone-Policy-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – Application-Based Internet Access Enforcement on Palo Alto NGFW](Application-Based-Internet-Access-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – SSL Forward Proxy on Palo Alto NGFW](SSL-Forward-Proxy-on-Palo-Alto-NGFW/)
- [Lab – Threat Prevention Enforcement on Palo Alto NGFW](Threat-Prevention-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – Vulnerability Protection Enforcement on Palo Alto NGFW](Vulnerability-Protection-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – DoS Protection on Palo Alto NGFW](DoS-Protection-on-Palo-Alto-NGFW/)
- [Lab – Inter-VLAN Segmentation on Palo Alto NGFW](Inter-VLAN-Segmentation-on-Palo-Alto-NGFW/)
- [Lab – Captive Portal User-ID Enforcement on Palo Alto NGFW](Captive-Portal-User-ID-Enforcement-on-Palo-Alto-NGFW/)
- [Lab – Policy-Based Forwarding Path Override on Palo Alto NGFW](Policy-Based-Forwarding-Path-Override-on-Palo-Alto-NGFW/)
- [Lab – Destination NAT with Pre-NAT Security Policy Matching on Palo Alto NGFW](Destination-NAT-with-Pre-NAT-Security-Policy-Matching-on-Palo-Alto-NGFW/)
- [Lab – Site-to-Site IPsec VPN on Palo Alto NGFW](Site-to-Site-IPsec-VPN-on-Palo-Alto-NGFW/)
- [Lab – GlobalProtect Remote Access VPN on Palo Alto NGFW](GlobalProtect-Remote-Access-VPN-on-Palo-Alto-NGFW/)
- [Lab – Active/Passive HA Failover on Palo Alto NGFW](Active-Passive-HA-Failover-on-Palo-Alto-NGFW/)
- [Lab – External Syslog Forwarding on Palo Alto NGFW](External-Syslog-Forwarding-on-Palo-Alto-NGFW/)
