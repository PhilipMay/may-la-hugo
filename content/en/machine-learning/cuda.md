---
title: CUDA
---

- disable GPU usage
  - `export CUDA_VISIBLE_DEVICES=""`
  - `os.environ["CUDA_VISIBLE_DEVICES"] = ""`
- enable only GPU 0
  - `export CUDA_VISIBLE_DEVICES="0"`
  - `os.environ["CUDA_VISIBLE_DEVICES"] = "0"`
