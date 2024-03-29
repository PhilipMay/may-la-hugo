---
title: GnuPG
---

## Links
- The GNU Privacy Handbook: https://gnupg.org/gph/en/manual.html
- Man page: https://www.gnupg.org/documentation/manpage.html
- Options
  - agent options: https://www.gnupg.org/documentation/manuals/gnupg/Agent-Options.html
  - configuration options: https://www.gnupg.org/documentation/manuals/gnupg/GPG-Configuration-Options.html
  - protocol specific options: https://www.gnupg.org/documentation/manuals/gnupg/OpenPGP-Options.html
- GnuPG files: https://www.gnupg.org/documentation/manuals/gnupg/GPG-Configuration.html
- YubiKey-Guide: https://github.com/drduh/YubiKey-Guide

## Commands

### Keyserver Commands
- download key from keyserver: `gpg --recv-keys <key_id>`
- update all keys from keyserver: `gpg --refresh-keys`
- import key with all signatures: `gpg --recv-key --verbose --keyserver-options no-import-clean --keyserver-options no-self-sigs-only <key_id>`

### Get Key Infos
- list all keys: `gpg --list-keys`
- list all secret keys: `gpg --list-secret-keys`

## Key Card Commands (YubiKey)
- `gpg --card-edit`
- also see https://www.gnupg.org/howtos/card-howto/en/ch03s02.html

## Keyserver Links
- https://keyserver.ubuntu.com/
- https://keys.openpgp.org/
- https://pgp.mit.edu/

## Mac install
- install with `brew install gnupg pinentry-mac`
- set `pinentry-program /opt/homebrew/bin/pinentry-mac` in `~/.gnupg/gpg-agent.conf`

## Important Keys
- CAcert `A31D 4F81 EF4E BD07 B456 FA04 D2BB 0D01 65D0 FD58`: http://www.cacert.org/index.php?id=3
- Pierre Schmitz (Arch Linux packager) `3E80 CA1A 8B89 F69C BA57  D98A 76A5 EF90 5444 9A5C`: https://archlinux.org/download/
- Debian CD signing key:`DF9B 9C49 EAA9 2984 3258  9D76 DA87 E80D 6294 BE9B`: https://www.debian.org/CD/verify
- Tails: `A490 D0F4 D311 A415 3E2B  B7CA DBB8 02B2 58AC D84F`
  - https://tails.boum.org/install/expert/
  - https://tails.boum.org/news/signing_key_transition/
