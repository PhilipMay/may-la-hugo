---
title: Linux Commands
---

## User Management
- create a user and set password
  - `useradd <username> -m -s /bin/bash`
  - `passwd <username>`
- add user to group: `gpasswd -a <username> <group>`
- change to other user: `su - <user_name>`
- delete a user with home dir and mail spool: `userdel -r <username>`
- also see: <https://wiki.archlinux.org/index.php/users_and_groups#Other_examples_of_user_management>

## Hardware
- get info about GPU: `lshw -C display`
- get infos about CPU: `cat /proc/cpuinfo`
- get infos about CPU temperature and fans
  - needs package called: `lm-sensors`
  - the command is `sensors`
  - also see: <https://askubuntu.com/a/15833/478988>

## Proxy Handling

### SSH through a Proxy (to an EC2 instance in this example)
```bash
ssh -i <key_file>.pem <user>@<target_host_or_ip> -o "ProxyCommand=nc -X connect -x <proxy_ip>:<proxy_port> %h %p"
```

### SCP through a Proxy (to an EC2 instance in this example)
```bash
scp -i ~/.ssh/<key_file>.pem -o "ProxyCommand=nc -X connect -x <proxy_ip>:<proxy_port> %h %p" <file> <user>@<target_host_or_ip>:
```

## Special
- output to terminal and file: `command | tee <filename>`

### Rotate Terminal
- to the right: `echo 1 | sudo tee
  /sys/class/graphics/fbcon/rotate_all`
- to the left: `echo 3 | sudo tee
  /sys/class/graphics/fbcon/rotate_all`

## Administration
- reboot with timer (5 minutes) and message: `shutdown -r +5 "<message>"`
