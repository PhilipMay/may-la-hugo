---
title: Screen
---

## Commands
- open a session with name: `screen -S <session_name>`
- list sessions: `screen -ls`
- resume detached session: `screen -r <session_name>`

## Recover a 'lost' Screen Session
If your remote connection crashed while you had an open screen session
you have to detach it before you can reconnect. You do it this way:

Reattach a session and if necessary detach it first.
```bash
screen -rd <session_name>
```

## Rename a session
To rename a session do:
1. Attach to the session in question
2. Press `ctrl` + `a`
3. Type `:sessionname <your_session_name>` – yes, the first colon is
   needed there, no extra spaces
4. Type `enter`
