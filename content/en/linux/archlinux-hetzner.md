---
title: Archlinux on Hetzner Cloud with Btrfs
---

## Links
- https://wiki.archlinux.org/title/Installation_guide
- https://community.hetzner.com/tutorials/how-to-install-archlinux-on-a-hetzner-cloud-server
- https://wiki.archlinux.org/title/GRUB
- https://wiki.archlinux.org/title/Systemd-networkd

```bash
# boot rescue system
# ssh into rescue system

# download current bootstrap image from https://mirror.chaoticum.net/arch/iso/latest/
wget https://mirror.chaoticum.net/arch/iso/latest/archlinux-bootstrap-<date>-x86_64.tar.gz
wget https://mirror.chaoticum.net/arch/iso/latest/archlinux-bootstrap-<date>-x86_64.tar.gz.sig

# check PGP fingerprint: 0x54449A5C

# check signature
gpg --keyserver keyserver.ubuntu.com --keyserver-options auto-key-retrieve --verify archlinux-bootstrap-<date>-x86_64.tar.gz.sig

# --numeric-owner preserve UID and GID of files in case existing Linux system uses different numbers than Arch
# see https://wiki.archlinux.org/title/Install_Arch_Linux_from_existing_Linux#Method_A:_Using_the_bootstrap_tarball_(recommended)
tar xvfz archlinux-bootstrap-2023.01.01-x86_64.tar.gz --numeric-owner

# hack - see https://wiki.archlinux.org/title/Install_Arch_Linux_from_existing_Linux#Downloading_basic_tools
mount --bind root.x86_64 root.x86_64

./root.x86_64/usr/bin/arch-chroot root.x86_64
echo 'Server = https://mirror.chaoticum.net/arch/$repo/os/$arch' > /etc/pacman.d/mirrorlist
pacman-key --init
pacman-key --populate archlinux

# refresh package lists
pacman -Syyu

# install nano
pacman -S nano

# clean disk
blkdiscard -f /dev/sda

# fdisk
fdisk /dev/sda
# Disklabel type: gpt
# Device     Start      End  Sectors  Size Type
# /dev/sda1   2048     4095     2048    1M BIOS boot
# /dev/sda2   4096 39999487 39995392 19.1G Linux filesystem

# install Btrfs tools
pacman -S btrfs-progs

# Btrfs filesystem
mkfs.btrfs /dev/sda2
mount -o compress=zstd /dev/sda2 /mnt
btrfs subvolume create /mnt/@
btrfs subvolume create /mnt/@home
btrfs subvolume create /mnt/@snapshots
btrfs subvolume create /mnt/@var_log
umount /mnt
mount -o compress=zstd,subvol=@ /dev/sda2 /mnt
mkdir /mnt/home
mount -o compress=zstd,subvol=@home /dev/sda2 /mnt/home
mkdir -p /mnt/var/log
mount -o compress=zstd,subvol=@var_log /dev/sda2 /mnt/var/log

# what about
# /var/cache/pacman/pkg or just /var/cache/pacman
# /var/lib/portables
# /var/lib/machines

# more mount options https://wiki.archlinux.org/title/Security#Mount_options

# pacstrap with -M option:
# -M is to "Avoid copying the host’s mirrorlist to the target."
pacstrap -G -M /mnt base grub linux linux-firmware openssh nano btrfs-progs

genfstab -U /mnt >> /mnt/etc/fstab
nano /mnt/etc/fstab
# remove all space_cache and subvolid entries

arch-chroot /mnt
ln -sf /usr/share/zoneinfo/Europe/Berlin /etc/localtime
hwclock --systohc
nano /etc/locale.gen
# uncomment en_US.UTF-8 UTF-8
locale-gen
nano /etc/locale.conf
# add LANG=en_US.UTF-8
nano /etc/vconsole.conf
# add KEYMAP=de-latin1
nano /etc/hostname
# add hostname

# Btrfs
nano /etc/mkinitcpio.conf
add btrfs to MODULES

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
exit
reboot
```

## Post Install

### Pacman
```bash
nano /etc/pacman.conf
# uncomment Color, VerbosePkgLists and ParallelDownloads

# init pacman
nano /etc/pacman.d/mirrorlist

pacman-key --init
pacman-key --populate archlinux

# refresh package lists
pacman -Syyu
```

### Install snapper
```bash
pacman -S snapper
snapper -c root create-config /
btrfs subvolume delete /.snapshots
mkdir /.snapshots
# edit /etc/fstab and mount /@snapshots to /.snapshots
mount /.snapshots
# reboot and see if all is mounted

# first manual test snapshot
snapper -c root create --description test01

# check if snapshot is stored
ls -ls /.snapshots

# install snap-pac to let pacman automatically use snapper to create pre/post snapshots
# install grub-btrfs to be able to boot from snapshots
pacman -S snap-pac grub-btrfs

# the grub main menu needs to be generated to make a menuentry for the snapshots sub menu
# see https://github.com/Antynea/grub-btrfs#-usage
grub-mkconfig -o /boot/grub/grub.cfg

# enable daemon script that automatically updates the grub menu when it sees a snapshot being created or deleted
# see https://github.com/Antynea/grub-btrfs#systemd-instructions
systemctl enable --now grub-btrfsd
```

### Other
```bash
# enable periodic TRIM
# see https://wiki.archlinux.org/title/Solid_state_drive#Periodic_TRIM
systemctl enable --now fstrim.timer
```

### Other Post Install Todo
- secure sshd
- check if TRIM and ssd options are correct
  - https://wiki.archlinux.org/title/btrfs#SSD_TRIM
  - https://wiki.archlinux.org/title/Solid_state_drive#Periodic_TRIM
  - https://btrfs.readthedocs.io/en/latest/Trim.html
  - https://btrfs.readthedocs.io/en/latest/btrfs-man5.html#mount-options
- setup sudo and secure root
- apply general recommendations: https://wiki.archlinux.org/title/General_recommendations
- apply security: https://wiki.archlinux.org/title/Security
- check "system maintenance": https://wiki.archlinux.org/title/System_maintenance
- no `fsck` in hooks (mkinitcpio)?
