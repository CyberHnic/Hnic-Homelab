# Windows and Ubuntu integration

## Goal

Integrate Parallels-hosted Windows and Ubuntu VMs with lab administration and storage services.

## Completed work

- Installed and configured SSH services on Windows and Ubuntu.
- Established SSH access from the Mac; Windows key-based access was verified with a non-interactive hostname command.
- Configured local `home.arpa` name resolution for the VMs.
- Mapped the NAS SMB share as a Windows drive.
- Checked Ubuntu addressing, gateway and DNS behavior.

## Troubleshooting

Local DNS records initially resolved through a test resolver port but not through the standard DNS service. After service/cache handling, resolution worked through the standard port.

Windows WSL attempts encountered platform virtualization limitations. Working WSL is not claimed as a completed outcome.

## Evidence to add

Sanitized SSH hostname output, DNS lookup results and a shared-file read/write test. Record which VM and operating-system build produced each result, since the environment changed during setup.

## Lessons

Validate DNS on the resolver port clients actually use. Account-specific Windows SSH key handling and service permissions can differ from Linux. Keep VM platform limitations separate from network faults.
