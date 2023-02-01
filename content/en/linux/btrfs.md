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
  - [Incremental Backup](https://btrfs.wiki.kernel.org/index.php/Incremental_Backup)
- Read the Docs: https://btrfs.readthedocs.io/
  - man pages: https://btrfs.readthedocs.io/en/latest/man-index.html
  - mount options: https://btrfs.readthedocs.io/en/latest/btrfs-man5.html#mount-options
- Btrfs @ Arch Linux: https://wiki.archlinux.org/title/btrfs
- Videos and Talks
  - Linuxcon Japan 2014 - Btrfs Talk
    - YouTube: https://www.youtube.com/watch?v=ND3OKCP70_I
    - Slides: http://marc.merlins.org/linux/talks/Btrfs-LC2014-JP/Btrfs.pdf
  - Btrfs is awesome except when it isn't (2019) - many good disaster recovery hints: https://www.youtube.com/watch?v=qHalOdCZO9Q
  - btrfs: The Best Filesystem You've Never Heard Of (2017): https://www.youtube.com/watch?v=-m01x3gHNjg
  - TUT91782 Getting the most out of the btrfs filesystem (2017) - tech internals: https://www.youtube.com/watch?v=iwNg_fusT9A

## Tasks

### Check redundancy (after a replaced disk)
- use `btrfs filesystem usage -T <path>` to check if all data, metadata and system is not "single" stored
- fix this with `btrfs balance start -dconvert=raid1,soft -mconvert=raid1,soft /mnt/btrfs`
- see https://wiki.tnonline.net/w/Btrfs/Replacing_a_disk

## Commands

### balance
- see https://btrfs.readthedocs.io/en/latest/btrfs-balance.html
- filters
  - `soft`: when converting between profiles chunks that already have the target profile are left untouched

### replace
- see https://btrfs.readthedocs.io/en/latest/btrfs-replace.html
- `start` subcommand with `-r`: only read from srcdev if no other zero-defect mirror exists. (enable this if your drive has lots of read errors, the access would be very slow)

### Other Commands
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
