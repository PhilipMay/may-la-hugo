---
title: Ubuntu
---

## Package Management
- clean cache: `apt clean`
- list installed packages: `apt list --installed`
- list manually installed packages: `apt-mark showmanual`
- remove package with dependencies: `apt-get <remove/purge> --auto-remove <package_name>`
- list installed packages from a specific source: `aptitude search "?origin (<package_source>) ?installed"`

### Update the System
``` bash
# fetch list of available updates
apt update

# list packages that can be upgraded
apt list --upgradable

# install some updates - do not remove packages
apt upgrade
# or
# install updates - also remove packages if needed
apt full-upgrade

# remove any old packages no longer needed
apt autoremove
```

### .deb Files
- get info about a .deb file: `dpkg -I <package_name>.deb`
- list Content of a .deb File: `dpkg -c <package_name>.deb`

## Configuration
- Proxy settings for all users in `/etc/environment` - also see https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-configure-proxy-on-ubuntu-18-04/

## Commands
- vheck ubuntu version: `lsb_release -a`

## Install Ubuntu as a VirtualBox Guest
This describes how to install Ubuntu as a VirtualBox guest system to do
experiments with docker or other stuff.

### Basic installation
- download a server version of Ubuntu
- the current LTS version might be a good idea
- do normal installation

### Install XFCE
To be able to copy and paste to and from the guest system you need a
desktop environment like XFCE. XFCE is small compared to GNOME and the
minimal installation does not contain LibreOffice and other stuff you do
not need.
- install tasksel: `sudo apt install tasksel`
- execute tasksel: `sudo tasksel`
- select `Xubuntu minimal installation`
- press tabulatur and select `Ok` with return key
- reboot

### Install VirtualBox Guest Additions
- `apt install build-essential dkms`
- link the VirtualBox Guest Additions iso image to a cd drive
- cd should be auto mounted to somewhere at `/media` if XFCE or GNOME
  is installed
- change to that directory and execute installation: `sudo
  ./VBoxLinuxAdditions.run`
- also see here:
<https://askubuntu.com/questions/1035030/virtualbox-guest-additions-installation-problem/1047193#1047193>

## Install Docker
To install docker do not install the package called `docker`. Docker is
a "System tray for KDE3/GNOME2 docklet applications". The package you
need is called `docker.io`
- install with: `sudo apt install docker.io`
- start with: `sudo systemctl start docker`
- stop with: `sudo systemctl stop docker`
- enable (always start at boot time) with: `sudo systemctl enable docker`
