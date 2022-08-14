---
title: Archlinux Installation
---

{{% alert title="To-do" color="info" %}}
Consolidate the old versions:

- https://github.com/PhilipMay/may-la-hugo/blob/8863faed26795c63e7daa97fb97b21b651be2d57/content/en/linux/arch-install.md
- https://wiki.archlinux.de/title/Benutzer:PMay/T430s_Setup

Also add
- GDM keyboard config
- firefox
- Gnome Keyboard config
- Gnome Terminal config
- Bootloader
- DISCARD - SSD
- Microcode
- update my PyCharm package
- good mirror list
{{% /alert %}}

## Bios Settings
- set the BIOS clock to GMT time zone
- turn all virtualization optiona on

## Keyboard Settings
- https://wiki.archlinux.org/title/installation_guide#Set_the_console_keyboard_layout
- German keyboard: `loadkeys de-latin1-nodeadkeys`

## Connect to W-Lan (TODO)
- see https://wiki.archlinux.org/title/Iwd#Connect_to_a_network
- `iwctl`
- `station <wlan_device> connect <ssid>`
- `exit`
- check with `ping archlinux.org`

## Disks
- show disk status `lsblk`
- delete disk if you have a SSD
  - also see: https://wiki.archlinux.de/title/Dm-crypt#Verschl.C3.BCsselung_anlegen
  - `blkdiscard -f /dev/nvme0n1`
  - also might want to use `--secure` or `-z/--zeroout` option - see https://wiki.archlinux.org/title/Solid_state_drive/Memory_cell_clearing#Common_method_with_blkdiscard

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

use `lsblk` to check if `cryptroot` is created

## Create and mount Filesystems
see also: <https://wiki.archlinux.org/index.php/EFI_system_partition#Format_the_partition>
```bash
mkfs.ext4 /dev/mapper/cryptroot
mount /dev/mapper/cryptroot /mnt
mkfs.fat -F 32 /dev/nvme0n1p1
mkdir /mnt/boot
mount /dev/nvme0n1p1 /mnt/boot
```

## Create Swap File (did not do this)
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
pacstrap /mnt nano gnome cryptsetup networkmanager
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
127.0.1.1	myhostname

nano /etc/mkinitcpio.conf

```
HOOKS=(base udev autodetect modconf block keyboard keymap encrypt filesystems fsck)
```

- see https://wiki.archlinux.org/title/Dm-crypt/System_configuration#mkinitcpio
- added after "block" -> "keyboard keymap encrypt"
- no `consolefont`

mkinitcpio -P

passwd

# install systemd-boot
bootctl install

systemd-boot does not accept tabs for indentation, use spaces instead.

nano /boot/loader/entries/arch.conf

```
title     Arch Linux
linux     /vmlinuz-linux
initrd    /initramfs-linux.img
options   cryptdevice=UUID=701fea32-236d-49fd-a0f9-cb9f07c94703:cryptroot root=/dev/mapper/cryptroot rw
```

use cat to add UUID to file:
use the UUID of the base encryped partition ! NOT cryptroot

blkid >> /boot/loader/entries/arch-uefi.conf

- see https://wiki.archlinux.org/title/Systemd-boot#Adding_loaders
- see https://wiki.archlinux.org/title/Dm-crypt/Encrypting_an_entire_system#Configuring_the_boot_loader

nano /boot/loader/entries/arch-uefi-fallback.conf

nano /boot/loader/loader.conf

```
#timeout 3
#console-mode keep
default        arch.conf
console-mode   max
editor         no
timeout        1
```

bootctl update

exit
cd /
umount -R /mnt
reboot

# create user
useradd <username> -m -s /bin/bash
passwd <username>

#gnome aktivieren
systemctl enable gdm.service
systemctl enable NetworkManager

reboot

# check heyboard layout at login!

# Gnome Settigs
- Keyboard
  - add German
  - remove en
- Mouse & Touchpad
  - Natural scolling aus
  - Tap to Click an
- check "Region & Language"
  - alle settings prüfen und synchronisieren
  - both tabs -> Language: English, Formats: all Deutschland
- Power
  - Automatic Suspend - on battery power und Plugged in aus
  - show percent


- als root ausführen: `localectl set-x11-keymap de`


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
