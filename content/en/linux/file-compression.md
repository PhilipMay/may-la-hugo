---
title: File Compression
---

## tgz
- compress: `tar cvfz <target_file>.tgz <source_files_or_dir>`
- fast compress: `tar -I pigz -cvf <target_file>.tgz <source_files_or_dir>`
- view files in archive: `tar -tf <filename>.tgz`

## zip
- test a zip archive: `unzip -t <filename>.zip`

## bz2
- unpack: `bzip2 -dk <filename>.bz2`

## gzip
- test `.gz` files: `gzip -v -t <file>.gz`
