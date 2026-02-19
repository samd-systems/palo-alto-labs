![Topology](topology.png)
![Failure](failure.png)
![Context](context.png)
![Validation](validation.png)


# Incident Case Study - Security Policy Rule Order Failure on Palo Alto NGFW

## Overview

This case study reproduces an incident where non-web traffic from the Trust zone was permitted to a DMZ web server due to security policy rule ordering. The behavior allowed RDP and ICMP sessions to establish across zones even though a web-only control was defined.

The content is documented as a validated engineering case note rather than a configuration walkthrough.

## Impact

Systems in the Trust zone were able to access the DMZ web server over RDP and ICMP. This bypassed the intended web-only segmentation boundary between internal users and the DMZ.

## Symptoms Observed

- RDP sessions from Trust to DMZ completed with action allow
- ICMP sessions from Trust to DMZ completed with action allow
- Traffic logs show rule match: Temp-Allow-Trust-to-DMZ
- Hit counter increased on the permissive rule
- The web-only rule did not match non-web applications

## Investigation Process

1. Filtered traffic logs for Trust-to-DMZ sessions.
2. Identified ms-rdp and ping sessions marked allow.
3. Correlated those sessions to Temp-Allow-Trust-to-DMZ.
4. Reviewed security policy ordering.
5. Confirmed the permissive rule was evaluated before the web-only rule.
6. Reviewed hit counters on both rules and confirmed only the permissive rule incremented.

## Root Cause

A temporary broad Trust-to-DMZ allow rule was positioned above the restrictive Trust-to-DMZ-Web-Only rule, causing first-match evaluation to allow all Trust-to-DMZ sessions during session setup.

## Resolution

The Temp-Allow-Trust-to-DMZ rule was disabled and logging was enabled on the interzone-default deny rule to restore segmentation enforcement and improve visibility.

## Validation After Fix

- RDP from Trust to DMZ denied under interzone-default
- ICMP from Trust to DMZ denied under interzone-default
- HTTP (web-browsing, port 80) allowed under Trust-to-DMZ-Web-Only
- HTTPS (SSL, port 443) allowed under Trust-to-DMZ-Web-Only
- Traffic logs confirm correct rule match behavior and deny/allow enforcement

## Engineering Lessons

- Rule order directly determines which policy is applied when a session is created.
- Temporary permissive rules can override intended segmentation when rule order is not revalidated after changes.
- Hit counters and session logs provide immediate visibility into rule precedence behavior.

## Lab Environment

- Palo Alto NGFW
  - eth1/1 Outside
  - eth1/2 Inside - Trust zone (10.10.10.0/24)
  - eth1/3 DMZ (172.16.0.0/24)
- Client workstation
- Web Server
- EVE-NG lab environment

## Status

Validated and complete.
