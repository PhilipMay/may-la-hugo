---
title: GnuPG
---

## Links
- The GNU Privacy Handbook: https://gnupg.org/gph/en/manual.html
-  YubiKey-Guide: https://github.com/drduh/YubiKey-Guide

## Get Infos
- list all keys: `gpg --list-keys`
- list all secret keys: `gpg --list-secret-keys`

## Mac install
- install with `brew install gnupg pinentry-mac`
- set `pinentry-program /opt/homebrew/bin/pinentry-mac` in `~/.gnupg/gpg-agent.conf`
