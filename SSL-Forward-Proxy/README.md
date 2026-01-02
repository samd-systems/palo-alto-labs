![Topology](topology.png)

![Validation](validation-1.png)

![Validation](validation-2.png)

# Lab – SSL Forward Proxy Decryption and Certificate Substitution

## Overview
This lab demonstrates SSL forward proxy behavior by observing certificate issuance changes during outbound HTTPS sessions. SSL forward proxy decryption was intentionally configured on the firewall to enable controlled interception of outbound encrypted traffic for validation purposes. Baseline passthrough traffic and intercepted traffic are compared using direct client-side inspection.

This lab is documented as a validated engineering case note rather than a configuration walkthrough.

## Lab Objectives
- Validate HTTPS passthrough behavior prior to decryption
- Observe firewall-issued certificates during SSL interception
- Confirm client-visible certificate substitution
- Verify SSL forward proxy behavior without relying on configuration artifacts

## Topology Summary
The topology consists of an internal client host traversing a Palo Alto Networks NGFW to reach external internet services. The firewall operates inline as an SSL forward proxy while management traffic remains isolated from the dataplane.

## Configuration Summary
- SSL forward proxy decryption enabled
- Firewall-generated certificate authority configured
- Decryption policy applied to outbound HTTPS traffic

(Configuration details intentionally omitted; focus is on behavior and validation.)

## Validation and Results

### Behavior Without the Control
Prior to SSL interception, HTTPS traffic passed through the firewall without decryption. The client observed certificates issued by public certificate authorities, confirming baseline passthrough behavior.

### Behavior With the Control
When SSL forward proxy interception occurred, the firewall substituted certificates issued by its own certificate authority. This change was observable directly at the client, confirming active SSL interception.

## Key Takeaways
- SSL forward proxy interception is observable through certificate issuer changes
- Baseline passthrough and intercepted behavior are clearly distinguishable
- Certificate handling is central to SSL inspection controls

## Lab Environment
- Palo Alto Networks NGFW (VM-Series)
- Client workstation
- EVE-NG virtual lab platform

## Status
Validated and complete.
