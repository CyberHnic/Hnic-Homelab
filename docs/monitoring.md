# Service and storage monitoring

## Implementation

Deployed Uptime Kuma in Docker on a Debian Raspberry Pi to monitor services. Added Monit checks on the Debian NAS for filesystems and SMART health.

## Fault and repair

SMART checks failed under Monit's systemd service restrictions. Added a service override with the capabilities required by the checks, reloaded systemd and restarted Monit. The subsequent summary was reported as healthy.

## Recorded validation

- The Uptime Kuma container reported healthy.
- Phone access to the dashboard was restored after access troubleshooting.
- Monit checks reported healthy following the SMART permissions repair.

## Next evidence

Collect sanitized service-status output and show one intentional failure and recovery. Review the capability set for the smallest permissions the deployed checks need. Capture backup and recovery documentation for monitoring data.

Grafana is being developed separately; dashboard and alerting claims should be added after the queries and behavior are verified.

## Lessons

A healthy container is only one layer of validation. Check that clients can access the dashboard and that individual checks detect the conditions they are meant to monitor.
