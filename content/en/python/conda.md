---
title: Conda
---

# Conda

## Manage Environments
- create environment: `conda create --name <new_env_name>`
- create environment with python 3.9: `conda create --name <new_env_name> python=3.9`
- activate environment: `conda activate <env_name>`
- deactivate (leave) environment: `conda deactivate`
- list available environments: `conda info --envs`
- remove environment: `conda remove --name <env_name> --all`

## Updates
- update conda: `conda update -n base -c defaults conda`
- update all conda packages in current environment: `conda update --all`
- also see: <https://docs.conda.io/projects/conda/en/latest/commands/update.html>

## Other Commands
- remove unused cached packages: `conda clean -a` - also see: <https://docs.conda.io/projects/conda/en/latest/commands/clean.html>
- disable automatic base activation: `conda config --set auto_activate_base false` - also see: <https://stackoverflow.com/a/54560785/271118>

## Rename Conda Environment
Rename `<src_env>` to `<target_env>`:
```text
conda create --name <target_env> --clone <src_env>
conda remove --name <src_env> --all
```

## Installation

### Conda installation on Linux
- download Conda (Python 3.x, Linux, 64-bit): <https://conda.io/miniconda.html>
- make install file executable: `chmod +x Miniconda3-latest-Linux-x86_64.sh`
- start installation: `./Miniconda3-latest-Linux-x86_64.sh`
- use default settings
- log out and back in to activate new settings

### Windows Install
- download Miniconda (not Anaconda): <https://conda.io/en/latest/miniconda.html>
- download Python 3.x with 64-bit and not 2.x or 32-bit version
- proxy setup
  - add the following content to the `.condarc` file
  - located at `C:\Users\<User>`
  - user and pass are optional
  - some https settings use the http protocol and not https
```text
proxy_servers:
  http: http://user:pass@corp.com:8080
  https: https://user:pass@corp.com:8080
```
