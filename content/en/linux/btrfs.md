---
title: Btrfs
---

## Links
- Wiki: https://btrfs.wiki.kernel.org/index.php/Main_Page
  - [Getting started](https://btrfs.wiki.kernel.org/index.php/Getting_started)
  - [FAQ](https://btrfs.wiki.kernel.org/index.php/FAQ)
  - [UseCases / Recipes](https://btrfs.wiki.kernel.org/index.php/UseCases)
  - [Sysadmin Guide](https://btrfs.wiki.kernel.org/index.php/SysadminGuide)
  - [Multiple Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)
  - [Problem FAQ](https://btrfs.wiki.kernel.org/index.php/Problem_FAQ)
  - [Gotchas](https://btrfs.wiki.kernel.org/index.php/Gotchas)
- Read the Docs: https://btrfs.readthedocs.io/
  - man pages: https://btrfs.readthedocs.io/en/latest/man-index.html
  - mount options: https://btrfs.readthedocs.io/en/latest/btrfs-man5.html#mount-options
- Btrfs @ Arch Linux: https://wiki.archlinux.org/title/btrfs

## Commands
```bash
# create raid1
mkfs.btrfs -m raid1 -d raid1 /dev/sda1 /dev/sdb1

# mount
mkdir /mnt/btrfs
mount -o compress=zstd /dev/sda1 /mnt/btrfs

# scrub
btrfs scrub start /mnt/btrfs
btrfs scrub status /mnt/btrfs

# show filesystem
btrfs filesystem show

# pull one drive and scrub + show

# replace disk 1
btrfs replace start 1 /dev/sdc1 /mnt/btrfs -f
btrfs replace status /mnt/btrfs

# device stats
btrfs device stats /mnt/btrfs
```
