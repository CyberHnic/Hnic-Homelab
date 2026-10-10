# Debian NAS and scheduled backups

## Goal

Provide shared storage for the lab and automate copying its contents to a separate drive.

## Implementation

Deployed Debian on an Intel NUC. Configured an ext4 data disk mounted at `/srv/storage`, an SMB share and a separate Samsung T5 backup drive mounted at `/mnt/t5-backup`.

An rsync-based script at `/usr/local/sbin/t5-backup.sh` copies storage to `/mnt/t5-backup/storage-backup`. A systemd timer schedules it daily at 03:00, with a log at `/var/log/t5-backup.log`. The exact script is not included in this draft.

## Recorded outcome

Shared storage was accessible from client systems, including a Windows mapped drive and an Android file manager. Backup automation was configured, and filesystem/SMART monitoring was added.

## Validation still to document

- Capture timer state, last execution result and a sanitized backup log.
- Verify the expected backup mount is present before a copy runs.
- Restore selected files into a temporary directory and compare contents.
- Document how the backup behaves when the destination drive is unavailable.

## Limitations and lessons

A separate local backup drive is useful but is not an off-site copy. The script's deletion and version-retention behavior must be reviewed before describing it as protection from accidental deletion. Successful copy execution also does not establish restore success.
