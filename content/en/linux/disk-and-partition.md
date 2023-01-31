---
title: Disk and Partition Management
---

## Useful Commands
- get disk UUID (for fstab): `blkid`
- filesystem check: `e2fsck -vf /dev/<disk>`
- delete all filesystems on disk: `wipefs -a <device>`

## Mount
- mount disk or patition: `mount /dev/sdb1 /mnt`
- mount everything defined in `/etc/fstab`: `mount -a`

## Backup with `dd`
- https://wiki.archlinux.org/title/Dd
- backup a disk (or snapshot) to a file: `dd if=/dev/<disk> bs=64K status=progress | gzip -c  > <backup_name>.img.gz`
- backup a disk (or snapshot) to a file (with parallel gzip): `dd if=/dev/<disk> bs=64K status=progress | pigz -c  > <backup_name>.img.gz`
- restore a backup to disk: `gunzip -c <backup_name>.img.gz | dd of=/dev/<disk>`

## LVM
- see https://wiki.archlinux.org/title/LVM
- see https://wiki.archlinux.org/title/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS

### Creation Commands
- create the pv and the vg in a primary partition and not a bare disk
- create physical volume: `pvcreate /dev/<partition>`
- create volume group: `vgcreate <volume_group_name> /dev/<partition>` (same `<partition>` as for the physical volume)
- create logical volume with fixed size: `lvcreate -L <size>G <volume_group_name> -n <logical_volume_name>`
- create logical volume with percentage of free size (100 for remaining size): `lvcreate -l <size_in_percent>%FREE <volume_group_name> -n <logical_volume_name>`
- format with ext4: `mkfs.ext4 /dev/<volume_group_name>/<logical_volume_name>`

### List Commands
- list physical volumes: `pvs`
- list volume groups: `vgs`
- list logical volumes: `lvs`
- details about volume groups (including allocated and remaining space): `vgdisplay`
- details about logical volumes: `lvdisplay`

### Snapshots
- https://wiki.archlinux.org/title/LVM#Snapshots
- create snapshot: `lvcreate --size <size>G --snapshot --name <snapshot_name> /dev/<volume_group_name>/<logical_volume_name>`
- revert to state of snapshot: `lvconvert --merge /dev/<volume_group_name>/<logical_volume_name>`
- delete snapshot: `lvremove /dev/<volume_group_name>/<snapshot_name>`

### Recover from Image of Snapshot
- create snapshot of disk to recover
  - that snapshot must be a bit larget than the disk
  - if it is smaller or same size this might happen at merge time: `Unable to merge invalidated snapshot LV vg1/restore_test`
  - "[...] a small amount of the space you allocate to the snapshot is used to track the locations of the chunks of data, so you should allocate slightly more space than you actually need [...]" - see https://linux.die.net/man/8/lvcreate
- use `dd` to copy image to snapshot
- merge snapshot

### Enlarge a Logical Volume
- https://wiki.archlinux.org/title/LVM#Resize_physical_volume
- https://wiki.archlinux.org/title/Resizing_LVM-on-LUKS
- add size and resize filesystem in one command: `lvresize -L +<additional_size>G --resizefs <volume_group_name>/<logical_volume_name>`
- set new size and resize filesystem in one command: `lvresize -L <additional_size>G --resizefs <volume_group_name>/<logical_volume_name>`
- change size in two steps:
  - add size logical volume: `lvresize -L +<size>G <volume_group_name>/<logical_volume_name>`
  - set new size of logical volume: `lvresize -L <size>G <volume_group_name>/<logical_volume_name>`
  - resize filesystem: `resize2fs /dev/<volume_group_name>/<logical_volume_name>`

## Other Disk Tools / Commands
- see disk activity
  - Debian: `apt-get install iotop`
  - command: `iotop -o -P -d 2`
- remove Kubernetes filesystems from `df`: `df -x overlay -x tmpfs -h`
