# WireGuard access from a phone

## Goal and implementation

Configure a WireGuard peer on OPNsense so an Android phone can reach home services remotely. Added the peer, tunnel addressing and client configuration, then tested access to local services.

## Recorded outcome

Successful tunnel pings and access to the OPNsense web interface were reported during the lab work. Storage access was also established on the phone using a file manager.

## Evidence to collect

- A dated test with Wi-Fi disabled to establish access over the mobile network.
- A sanitized peer-status view with a recent handshake.
- Explicit results for each permitted home service.
- Current DNS and route settings, without private keys or public endpoint details.

## Lessons

Tunnel establishment, DNS and application access each require their own check. Keep server configuration and client profiles consistent, and validate remote access from outside the home network.
