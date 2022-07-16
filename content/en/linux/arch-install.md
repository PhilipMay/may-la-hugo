---
title: Archlinux Installation
---

# Archlinux Installation

## Bios Settings (TODO)

## Time Settings (TODO)

## Keyboard Settings
```bash
loadkeys de-latin1-nodeadkeys
```

## Connect to W-Lan (TODO)

## Show Disk Status
```bash
lsblk
```

## Delete Disk if you have SSD
also see: <https://wiki.archlinux.de/title/Dm-crypt#Verschl.C3.BCsselung_anlegen>
```bash
blkdiscard /dev/nvme0n1
```

## Check if Disk is clean now
```bash
lsblk
```

## Create partitions
see also: (TODO)
```bash
gdisk /dev/nvme0n1
```
- create 512MB boot / EFI - type: ef00
- rest for root (LUKS) - type: 8309

## Show Disk Status
```bash
lsblk
```

## Create LUKS
```bash
cryptsetup luksFormat /dev/nvme0n1p2
cryptsetup open /dev/nvme0n1p2 cryptroot
```

## Create and mount Filesystems
see also: <https://wiki.archlinux.org/index.php/EFI_system_partition#Format_the_partition>
```bash
mkfs.ext4 /dev/mapper/cryptroot
mount /dev/mapper/cryptroot /mnt
mkfs.fat -F32 /dev/nvme0n1p1
mkdir /mnt/boot
mount /dev/nvme0n1p1 /mnt/boot
```

## Create Swap File
see also: <https://wiki.archlinux.org/index.php/Swap#Swap_file_creation>
- TODO: Link zu Ubuntu Seite
```bash
dd if=/dev/zero of=/swapfile bs=1M count=20480 status=progress
chmod 600 /mnt/swapfile
mkswap /mnt/swapfile
swapon /mnt/swapfile
```

To resume from swap see: <https://wiki.archlinux.org/index.php/Power_management/Suspend_and_hibernate#Hibernation_into_swap_file>

## Select Mirrors
```bash
nano /etc/pacman.d/mirrorlist
```

## Install Packages
``` bash
pacstrap /mnt base linux linux-firmware
pacstrap /mnt nano gnome cryptsetup
pacstrap /mnt efibootmgr dosfstools gptfdisk
```

```
# gen and check fstab
genfstab -U /mnt >> /mnt/etc/fstab
less /mnt/etc/fstab

#Chroot
arch-chroot /mnt

#Time zone
ln -sf /usr/share/zoneinfo/Europe/Berlin /etc/localtime
hwclock --systohc

nano /etc/locale.gen
- remove comment for de_DE UTF-8
- remove comment for en_US UTF-8
locale-gen
nano /etc/locale.conf

# see: http://www.gentoo.org/doc/en/guide-localization.xml#doc_chap3
LANG="en_US.UTF-8"
LC_TIME="de_DE.UTF-8"

nano /etc/vconsole.conf
KEYMAP=de-latin1-nodeadkeys

nano /etc/hostname
- enter hostname

nano /etc/hosts

127.0.0.1	localhost
::1		localhost
127.0.1.1	myhostname.localdomain	myhostname

nano /etc/mkinitcpio.conf

- TODO: add content

mkinitcpio -P

passwd

# install systemd-boot
bootctl install

nano /boot/loader/entries/arch-uefi.conf
nano /boot/loader/entries/arch-uefi-fallback.conf
nano /boot/loader/loader.conf

# TODO: add content later

bootctl update

exit
umount -R /mnt
reboot

# create user
useradd <username> -m -s /bin/bash
passwd <username>

#gnome aktivieren
systemctl enable gdm.service
systemctl enable NetworkManager

reboot

# microcode
# https://wiki.archlinux.org/index.php/Microcode
pacman -S amd-ucode
# add in boot config
initrd  /cpu_manufacturer-ucode.img

# fstrim
systemctl enable fstrim.timer

# swappiness
# https://wiki.archlinux.org/index.php/Swap#Swappiness
nano /etc/sysctl.d/99-swappiness.conf

vm.swappiness=10

# sudo
pacman -S sudo
EDITOR=nano visudo
%wheel      ALL=(ALL) ALL
gpasswd -a <username> wheel

nano /etc/mkinitcpio.conf
MODULES=(amdgpu)
mkinitcpio -P

# enable aur
pacman -S --needed base-devel
nano /etc/makepkg.conf
```

## Lenovo ThinkPad T495x specific

### Mask this to avoid Boot Error
also see: <https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_T495s#Backlight>
``` bash
systemctl mask systemd-backlight@backlight:acpi_video0.service
```
