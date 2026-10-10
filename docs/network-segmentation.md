# Network segmentation with OPNsense

## Goal

Build a home environment with separate LAN, Guest and Lab networks while preserving access to the services each network needs.

## Implementation

Configured OPNsense interfaces and VLANs, a managed switch and an Omada access point. The lab uses VLAN 20 for Guest and VLAN 30 for Lab, alongside the main LAN. Wireless clients use the appropriate network gateway and DNS settings.

## Troubleshooting

During a connectivity incident, some clients could reach a public IP but could not reach local gateways or services. I used gateway pings, DNS checks and targeted port scans to distinguish internet connectivity from local access and name resolution. Connectivity to LAN services was restored after network repairs.

## Validation recorded

- Client addressing and gateways were inspected across the networks.
- Internet reachability and local service reachability were tested separately.
- LAN connectivity was reported working after the repair.

These observations do not prove complete isolation between VLANs. A dated test matrix for Guest-to-LAN denies and intentionally permitted flows remains to be added.

## Lessons

A successful public-IP ping does not prove that DNS or local access works. Validate each path separately and check switch tagging, client addressing and firewall rules together.
