---
title: Btrfs
---

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