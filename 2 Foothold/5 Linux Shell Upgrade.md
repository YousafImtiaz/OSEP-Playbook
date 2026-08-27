> If we need to stabilize a shell this one works most of the time:

```
python3 -c 'import pty;pty.spawn("/bin/bash")'
```

> Others we can try:

```
python -c 'import pty; pty.spawn("/bin/bash")'
```

```
/usr/bin/python3 -c 'import pty;pty.spawn("/bin/bash")'
```

If we use penelope shell handler it will auto stabilize the shell upon receiving a reverse shell connection.