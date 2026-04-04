![Topology](topology.png)
![Context](context.png)
![Failure](failure.png)
![Validation](validation.png)

# Incident Case Study - Zero Trust Policy Failure Allowing Unintended Server Zone Access on Palo Alto NGFW

This case study reproduces an incident where a GlobalProtect contractor user accessed a restricted Server Zone subnet through the VPN tunnel. The condition reflects a Zero Trust policy failure and introduced unintended reachability into protected infrastructure without any enforcement blocking the session.

The content is documented as a validated engineering case note rather than a configuration walkthrough.

## Impact

Unauthorized access was possible from GlobalProtect contractor users into the Server Zone. Critical server infrastructure within the Server Zone was exposed to contractor accounts. No deny logs or alerts were generated during the access window.

## Symptoms Observed

- GlobalProtect gateway session data showed contractor user assigned a tunnel IP
- Traffic logs showed sessions from GP-Tunnel-Zone to Server-Zone matched to GP-Tunnel-to-Server-Zone permit rule
- No deny logs recorded for GP-Tunnel-Zone to Server-Zone traffic
- No alerting triggered for contractor sessions

## Investigation Process

1. Verified GlobalProtect gateway session and user assignment
2. Reviewed GlobalProtect gateway current-user output for assigned user session
3. Verified assigned access routes from GlobalProtect gateway configuration
4. Correlated traffic logs with matching security policy
5. Reviewed GlobalProtect client profile configuration against intended access design

## Root Cause

Server Zone subnet was incorrectly included in the Contractor-Access-Profile split tunnel access routes during an IT user onboarding change window. A broad permit rule on the GP-Tunnel-to-Server-Zone policy, written without identity scoping, failed to act as a backstop, silently permitting the unintended access.

## Resolution

The Server Zone subnet was removed from the Contractor-Access-Profile split tunnel configuration and the GP-Tunnel-to-Server-Zone security policy was restricted to IT users only.

## Validation After Fix

- GlobalProtect gateway current-user output shows Contractor-Access-Profile assigned access routes no longer include the Server Zone subnet
- No new sessions observed from GP-Tunnel-Zone to Server-Zone for contractor accounts in traffic logs

## Engineering Lessons

- This pattern commonly occurs in enterprise GlobalProtect deployments during access profile changes such as onboarding new user groups, expanding remote access scope, or copying profiles as templates.
- Security policy must operate as an independent control layer because reachability and authorization are enforced separately.
- This is a Zero Trust implementation failure, not a configuration mistake. Enforcement layers are treated as compensating controls instead of independently validating access. No single control failed. The breakdown occurs in the interaction between controls.

## Lab Environment

- Palo Alto NGFWs
- Cisco switches
- Servers
- Client workstations
- EVE-NG lab environment

## Status

Validated and complete.
