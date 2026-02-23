![Topology](topology.png)
![Failure](failure.png)
![Validation](validation.png)
![Context](context.png)

# Incident Case Study - Security Zone Misconfiguration on Palo Alto NGFW

## Overview

This case study reproduces an incident where a zone misconfiguration removed segmentation boundaries between HR and internal servers, rendering an explicit deny policy inoperable. The condition resulted in unintended lateral access despite the presence of a correctly ordered deny rule.

The content is documented as a validated engineering case note rather than a configuration walkthrough.

## Impact

HR subnet gained unintended access to internal server assets including App-SRV-01 and AD-DC-01. Segmentation between HR-Zone and Server-Zone was not enforced, introducing lateral movement risk across sensitive infrastructure.

## Symptoms Observed

- HR users successfully accessed internal server resources.
- Traffic logs classified sessions as Server-Zone to Server-Zone.
- intrazone-default rule matched with action allow.
- Departments-to-Server-Deny rule recorded no hits.
- No deny logs were generated during initial access attempts.

## Investigation Process

1. Reviewed security policy order and verified deny rule placement.
2. Analyzed traffic logs to determine zone classification behavior.
3. Inspected subinterface configuration under Network > Interfaces > VLAN.
4. Identified the HR VLAN subinterface assigned to Server-Zone.
5. Confirmed both HR and Server subnets were mapped to the same zone.
6. Validated intrazone-default behavior as allow by design when traffic remains within a single zone.

## Root Cause

The VLAN 11 subinterface was assigned to Server-Zone instead of HR-Zone, causing HR to Server traffic to be evaluated as intrazone traffic.

## Resolution

The VLAN 11 subinterface was reassigned to HR-Zone and configuration changes were committed. Traffic flows were re-tested to validate segmentation enforcement.

## Validation After Fix

- HR to Server traffic classified as HR-Zone to Server-Zone.
- Departments-to-Server-Deny rule matched and enforced deny.
- HR to DMZ traffic matched Departments-to-DMZ-Web-Allow.
- No further intrazone-default matches were observed between HR and Server networks.

## Engineering Lessons

- This pattern commonly occurs during VLAN expansion or network segmentation redesign when interface mappings are modified without validating enforcement boundaries.
- Zone classification determines which policy path a session follows before rule evaluation.
- Segmentation validation must confirm both rule logic and interface-to-zone alignment; policy simulation tools alone will not detect zone boundary removal when rules themselves are correctly defined.

## Lab Environment

- Palo Alto NGFW
- Cisco switch
- Servers
- Client workstations
- EVE-NG lab environment

## Status

Validated and complete.
