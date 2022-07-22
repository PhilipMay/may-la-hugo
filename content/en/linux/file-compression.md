---
title: File Compression
---

## tgz
- compress: `tar cvfz <target_file>.tgz <source_files_or_dir>`
- fast compress (does not work): `tar -I pigz -cvf <source_files_or_dir> <target_file>.tgz`
- view files in archive: `tar -tf <filename>.tgz`

## zip
- test a zip archive: `unzip -t <filename>.zip`

## bz2
- unpack: `bzip2 -dk <filename>.bz2`
