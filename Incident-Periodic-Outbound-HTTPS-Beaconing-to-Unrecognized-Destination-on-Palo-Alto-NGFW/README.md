![Topology](topology.png)
![Failure](failure.png)
![Validation](validation.png)
![Context](context.png)

# Incident Case Study - Periodic Outbound HTTPS Beaconing to Unrecognized Destination on Palo Alto NGFW

This case study reproduces an incident where outbound HTTPS sessions were observed from an internal host to an unrecognized external destination. The traffic remained classified only as ssl with no higher-layer application identification.

The content is documented as a validated engineering case note rather than a configuration walkthrough.

## Impact

It was difficult to determine whether the repeated outbound communication to the external destination represented normal or potentially malicious activity.

## Symptoms Observed

- Outbound sessions were classified as ssl and allowed by the Outbound-Allow rule
- Sessions were short-lived, low-volume, and occurred at consistent intervals
- Threat Prevention profiles were active on the permitting rule, but no alerts were generated
- Destination was not associated with any recognized or expected external service

## Investigation Process

1. Reviewed traffic logs filtered by source IP to confirm session flow between the internal host and the external destination.
2. Correlated log timestamps to identify a consistent interval pattern in outbound session initiation.
3. Analyzed session details including duration and byte count to confirm connections were short-lived and low-volume.
4. Investigated the external destination against known services and confirmed it did not align with expected communication.

## Root Cause

Outbound HTTPS traffic was permitted by policy without sufficient inspection to identify the underlying application, allowing recurring sessions to an unrecognized external destination to persist.

## Resolution

Inspection policy scope was extended for the affected outbound path to improve traffic visibility. A targeted deny rule was implemented to block the suspicious external destination. An External Dynamic List was implemented and enforced through security policy to block additional untrusted destinations.

## Validation After Fix

- Traffic to the external destination was denied after policy enforcement
- Deny actions were recorded in traffic logs for subsequent connection attempts
- External Dynamic List matches were observed in policy logs for the blocked destination

## Engineering Lessons

- This pattern commonly occurs in segmented enterprise networks where outbound HTTPS traffic is broadly permitted to support user activity, system updates, and application access across departments and network zones such as IT or server segments.
- In these environments, decryption coverage is often absent on specific outbound traffic paths, allowing recurring low-volume connections to unrecognized external destinations to blend into normal encrypted traffic and persist without detection.
- Addressing this requires evaluating whether inspection gaps on affected traffic paths are intentional or unaddressed, and applying controls such as External Dynamic Lists where appropriate. With modern security appliances, improved coverage can be achieved without impacting normal operations where decryption is permitted.

## Lab Environment

- Palo Alto NGFWs
- Cisco switches
- Servers
- Client workstations
- EVE-NG lab environment

## Status

Validated and complete.
