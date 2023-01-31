---
title: Archlinux on Hetzner Cloud
---

## Links
- https://wiki.archlinux.org/title/Installation_guide
- https://community.hetzner.com/tutorials/how-to-install-archlinux-on-a-hetzner-cloud-server
- https://wiki.archlinux.org/title/GRUB
- https://wiki.archlinux.org/title/Systemd-networkd

```bash
# boot rescue system
# ssh into rescue system

# get network name
ip link
#1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
#    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
#2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
#    link/ether 96:00:01:da:19:a4 brd ff:ff:ff:ff:ff:ff
#    altname enp0s3
#    altname ens3

## I forgot sshd, network config and should also add ssh key

wget https://mirror.chaoticum.net/arch/iso/2023.01.01/archlinux-bootstrap-2023.01.01-x86_64.tar.gz
wget https://mirror.chaoticum.net/arch/iso/2023.01.01/archlinux-bootstrap-2023.01.01-x86_64.tar.gz.sig
gpg --keyserver keyserver.ubuntu.com --keyserver-options auto-key-retrieve --verify archlinux-bootstrap-2023.01.01-x86_64.tar.gz.sig

# check signature

tar xvfz archlinux-bootstrap-2023.01.01-x86_64.tar.gz
mount --bind root.x86_64 root.x86_64
./root.x86_64/usr/bin/arch-chroot root.x86_64
echo 'Server = https://geo.mirror.pkgbuild.com/$repo/os/$arch' > /etc/pacman.d/mirrorlist
pacman-key --init
pacman-key --populate archlinux

## fdisk
## Disklabel type: gpt
## Device     Start      End  Sectors  Size Type
## /dev/sda1   2048     4095     2048    1M BIOS boot
## /dev/sda2   4096 39999487 39995392 19.1G Linux filesystem

mkfs.ext4 /dev/sda2
mount /dev/sda2 /mnt
genfstab -U /mnt >> /etc/fstab
# check /etc/fstab

# pacstrap with -M option:
# -M is to "Avoid copying the host’s mirrorlist to the target."
pacstrap -G -M /mnt base grub linux linux-firmware openssh nano

arch-chroot /mnt
ln -sf /usr/share/zoneinfo/Europe/Berlin /etc/localtime
nano /etc/locale.gen
# uncomment en_US.UTF-8 UTF-8
nano /etc/locale.conf
# add LANG=en_US.UTF-8
nano /etc/vconsole.conf
# add KEYMAP=de-latin1
nano /etc/hostname
# add hostname

mkinitcpio -P

# set root password
passwd

# install GRUB
# use /dev/sda not /dev/sda1 or /dev/sda2
grub-install --target=i386-pc /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg

# systemd-networkd
nano /etc/systemd/network/20-wired.network
# add
[Match]
Type=ether

[Network]
DHCP=yes

# enable network
systemctl enable systemd-networkd
systemctl enable systemd-resolved

# enable sshd
systemctl enable sshd

useradd mike -m -s /bin/bash
passwd mike

# logout & reboot
exit
reboot
```
