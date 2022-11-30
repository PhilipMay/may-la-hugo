---
title: SSH
---

## Config File

### Default Config
The default config looks like this
```text
Host <hostname> <ip>
   HostName <ip>
   User <username>
   IdentitiesOnly yes
   IdentityFile ~/.ssh/<sec_key_filename>
```

### Using a Jump Server
If you have a jump server <jump_server_hostname> write a normal config for both servers and add this to the config of the target server: `ProxyJump <jump_server_hostname>`

If you also want to connect through an HTTP proxy add the proxy config lines to the config of the jump server.

### Connect through HTTP proxy
For Linux add this:
```text
   ProxyCommand nc -X connect -x <proxy_ip>:<proxy_port> %h %p
   ForwardAgent yes
```

For Windows (git bash) add this:
```text
   ProxyCommand connect -H <proxy_ip>:<proxy_port> %h %p
   ForwardAgent yes
```

## SSH Tunnel
- <https://www.ssh.com/ssh/tunneling>
- <https://wiki.archlinux.org/index.php/HTTP_tunneling>
- <http://www.netzmafia.de/skripten/internet/ssh-tunnel.html>
- <https://www.heise.de/tipps-tricks/SSH-Tunnel-nutzen-so-geht-s-4320041.html>
