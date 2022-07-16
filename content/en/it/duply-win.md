---
title: Duply with Windows
---

## Installation
  - install cygwin: <https://cygwin.com/>
  - first just install base packages
  - install the following additional packages (by just starting
    `setup-x86_64.exe` again):
      - python3
      - python36-pip
      - python3-devel
      - gcc-core
      - librsync-devel
      - gnupg2
      - nano
  - update `binutils` to newest (test) version (2.31.1-1)
  - update pip (optional): `pip3 install --upgrade pip`
  - install duplicity: `pip3 install duplicity`
  - create bin dir: `mkdir bin`
  - change to that dir: `cd bin`
  - create link to gpg2: `ln -s /usr/bin/gpg2.exe gpg.exe`
  - download duply: <https://duply.net/>
  - unpack duply
  - copy duply script to bin dir: `cp
    /cygdrive/c/Users/<your_username>/Downloads/<duply_dir>/duply .`
  - change back to home dir `cd`

## Configuration of .bashrc
  - edit .bashrc: `nano .bashrc`
  - add `export PATH=/home/<your_username>/bin:$PATH`
  - switch language to english (optional): `export LANG='en_US.UTF-8'`
  - add `ulimit -n 1024`

## Check Installation and configuration
The following commands should execute without error or warning: -
`duplicity --version` - `duply --version` - `gpg --version`

## Generate GPG Key
  - run `gpg --full-gen-key`
  - select default values but 4096 Bit
  - select a password for the key
  - copy the public key id to somewhere else for later use - it is a
    sring like `7A6E4278E2CAF3FA16240DADC94F3BEAB276F92D`

## Configure Duply
  - create a profile: `duply <profile_name> create`
  - edit config: `nano .duply/<profile_name>/conf`
      - enter your gpg public key it to `GPG_KEY`
      - enter the password to `GPG_PW`
      - enter the `TARGET` like a cloud space or something else
      - for `SOURCE` just enter `/` - details will be configured in an
        other file later
      - remove comment infront of `GPG_OPTS` and write
        `GPG_OPTS='--pinentry-mode loopback'`
  - edit exclude file: `nano .duply/<profile_name>/exclude`

This is how you can add your Cygwin home folder and your Windows
pictures folder to backup and ignore evenrything else `- **`

    + /home/<your_username>
    + /cygdrive/c/Users/<your_username>/Pictures
    - **

## Edit gpg-agent.conf
  - edit gpg-agent.conf: `nano .gnupg/gpg-agent.conf`
  - add this line: `allow-loopback-pinentry`

## Using Backblaze
  - install client: `pip3 install b2sdk`
  - use this as `TARGET`: `b2://[keyID]:[application key]@[B2 bucket
    name]`

## Start Backup
  - start the first backup: `duply test backup`
