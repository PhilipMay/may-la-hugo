---
title: GnuPG
---

## Links
- The GNU Privacy Handbook: https://gnupg.org/gph/en/manual.html
- Options
  - agent options: https://www.gnupg.org/documentation/manuals/gnupg/Agent-Options.html
  - configuration options: https://www.gnupg.org/documentation/manuals/gnupg/GPG-Configuration-Options.html
  - protocol specific options: https://www.gnupg.org/documentation/manuals/gnupg/OpenPGP-Options.html
- YubiKey-Guide: https://github.com/drduh/YubiKey-Guide

## Get Infos
- list all keys: `gpg --list-keys`
- list all secret keys: `gpg --list-secret-keys`

## Mac install
- install with `brew install gnupg pinentry-mac`
- set `pinentry-program /opt/homebrew/bin/pinentry-mac` in `~/.gnupg/gpg-agent.conf`
