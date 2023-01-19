---
title: ZFS
---

## Links
- https://openzfs.github.io/openzfs-docs/

## Commands
- list drive ids: `ls -l /dev/disk/by-id/`
- show status
  - list zpools: `zpool list` - shows raw capacity, to see real capacity use `zfs list`
  - see status of zpool: `zpool status`
- mirror handling
  - create mirror: `zpool create tank mirror <vdev_1> <vdev_2>`
  - add mirror: `zpool add tank mirror <vdev_1> <vdev_2>`
  - remove mirror: `zpool remove tank <mirror-id>` - get mirror-id with `zpool status`
- delete pool: `zpool destroy tank`
- dataset handling
  - create dataset: `zfs create <nameofzpool>/<nameofdataset>`
  - list datasets: `zfs list`
