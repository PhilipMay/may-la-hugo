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
- list running Services: `systemctl list-units --type=service`

## Journal
- delete old journal files (ony keep last 2 days): `journalctl --vacuum-time=2d`
