![Topology](topology.png)
![Context](context.png)
![Failure](failure.png)
![Validation](validation.png)

# Incident Case Study - Application-Based Policy Mismatch on Palo Alto NGFW

## Overview

This case study reproduces an incident where users reported inconsistent website accessibility. Standard HTTP traffic functioned normally, while HTTPS sessions failed. Encrypted web traffic was denied despite routing, NAT, and outbound web-browsing policy operating correctly.

This documentation is structured as a validated engineering case note rather than a configuration walkthrough.

## Impact

Users in the Inside zone experienced encrypted traffic failure. HTTPS sessions were denied while other outbound traffic succeeded, creating operational ambiguity and extending troubleshooting time.

## Symptoms Observed

- HTTPS sessions consistently failed while other outbound traffic succeeded  
- Encrypted traffic matched the default interzone deny rule  
- DNS resolution traffic was permitted  
- Traffic identified as web-browsing was allowed by the Inside-to-Outside rule  
- Successful outbound sessions confirmed routing and NAT functionality  

## Investigation Process

1. Reproduced the issue from an internal client.  
2. Correlated browser reset behavior to denied encrypted sessions.  
3. Confirmed HTTPS traffic did not match the intended outbound security rule.  
4. Validated routing and NAT through successful non-encrypted outbound sessions.  
5. Reviewed the Inside-to-Outside security policy.  
6. Identified missing encrypted application coverage.

## Root Cause

The Inside-to-Outside security policy allowed dns and web-browsing but excluded ssl, causing HTTPS sessions to match the default interzone deny rule.

## Resolution

Updated the Inside-to-Outside security rule to explicitly allow ssl and quic applications and committed the configuration.

## Validation After Fix

- Encrypted sessions successfully matched the Inside-to-Outside rule  
- Traffic logs reflected allow actions for ssl  
- Session termination behavior indicated normal TCP closure  
- HTTPS websites loaded successfully without reset behavior  

## Engineering Lessons

- Application-based policy gaps commonly occur during transitions from port-based rule design to App-ID-based enforcement or security hardening initiatives.  
- Application-default enforces port compliance but does not implicitly include related encrypted applications.  
- Policy intent should be validated against observed application behavior rather than assumed protocol relationships.  
- Monitoring default-rule deny logs for legitimate application traffic can surface outbound policy design gaps before they become user-facing incidents.

## Lab Environment

- Palo Alto NGFW  
- Cisco switch  
- Client workstation  
- EVE-NG lab environment  

## Status

Validated and complete.
