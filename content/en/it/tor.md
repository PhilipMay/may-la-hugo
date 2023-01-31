---
title: "Tor"
---

## Links
- https://www.torproject.org/
  - Relay Operations: https://community.torproject.org/relay/
  - Middle/Guard relay: https://community.torproject.org/relay/setup/guard/
  - Relay Post-install and good practices: https://community.torproject.org/relay/setup/post-install/

## Commands
- see log: `journalctl -e -u tor@default`
- restart tor: `systemctl restart tor@default`
- command-line Tor monitor: `nyx`

## Config
Config is stored at `/etc/tor/torrc`.

### Example middle / guard relay config
```
Nickname    my_nickname
ContactInfo mail _at_ host.com
ORPort      443
ExitRelay   0
SocksPort   0

# this does not work with AccountingMax
DirPort 9030

RelayBandwidthRate     9 MB
RelayBandwidthBurst    10 MB

MyFamily identity_key_fingerprint_01,identity_key_fingerprint_02
```

### Bridge config
A bridge helps censored users connect to the Tor network.
Do not specify `MyFamily` for bridge configs.

## Backup
After installation and start of the tor daemon it is a good idea to make a backup of your relay's long term identity keys.
They are located at: `/var/lib/tor/keys`
Best would be to backup all of `/var/lib/tor`.
