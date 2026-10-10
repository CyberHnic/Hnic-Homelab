# Recovering ProtonVPN policy routing

## Problem

After a reboot, expected VPN-routed traffic used the ISP connection instead. Internet access still worked, so connectivity alone did not reveal the routing fault.

## Work completed

Restored OPNsense policy routing for the selected lab sources and rebuilt the associated WAN egress protection. Checked the VPN gateway, source selection and generated firewall rules, including the WAN blocking tag used by the configuration.

## Validation recorded, 2–3 October 2026

- Traceroute from the tested Mac interface showed OPNsense followed by the Proton tunnel path.
- Two external IP checks returned a Proton exit address.
- IPv4 HTTPS requests to public services succeeded.
- Reboot persistence was checked and the expected VPN route remained in use.

The public addresses and raw outputs are omitted from this draft. These checks apply to the tested client and interface. A controlled tunnel-down test with dated output is still needed as public evidence that traffic cannot fall back to WAN.

## Example validation commands

Run on the intended client and record its interface and default gateway alongside the output:

```bash
traceroute -n 8.8.8.8
curl -4 --connect-timeout 10 https://ifconfig.me/ip
curl -4 --connect-timeout 10 https://api.ipify.org
curl -4 -I --connect-timeout 10 https://www.google.com
```

## Lessons

Check route selection, observed egress and reboot behavior together. An active tunnel does not establish that a particular client uses it. VPN egress validation and kill-switch validation are separate checks.
