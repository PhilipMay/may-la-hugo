---
title: Systemd
---

## Commands and Locations
- custom services are stored here: `/etc/systemd/system`
- analyse security of service unit: `systemd-analyze security <service_unit>`
- restart a service: `systemctl restart <application_name>.service`
- show logs of a service: `journalctl -u <application_name>.service`

## List Services
- list enabled services: `systemctl list-unit-files --state=enabled`
- list running services: `systemctl list-units --type=service`
- list failed services: `systemctl --failed`
- list timers: `systemctl list-timers`

## List all since boot
- all boot cycles: `journalctl -k -b all`
- current boot : `journalctl -k`
- last boot: `journalctl -k -b -1`
- two boots prior: `journalctl -k -b -2`
- and so on

## Journal
- delete old journal files (ony keep last 2 days): `journalctl --vacuum-time=2d`
