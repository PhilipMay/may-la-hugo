---
title: File Compression
---

## tgz
- compress
  - standard: `tar cvfz <target_file>.tgz <source_files_or_dir>`
  - fast: `tar -I pigz -cvf <target_file>.tgz <source_files_or_dir>`
  - fast: `tar -I "pigz --best" -cvf <target_file>.tgz <source_files_or_dir>`
- view files in archive: `tar -tf <filename>.tgz`
- test archive: `gunzip -t <filename>.tgz`
- test archive fast: `pigz -t <filename>.tgz` - pigz uses threads to make use of multiple processors and cores

## zip
- test a zip archive: `unzip -t <filename>.zip`

## bz2
- unpack: `bzip2 -dk <filename>.bz2`

## gzip
- test `.gz` files: `gzip -v -t <file>.gz`
