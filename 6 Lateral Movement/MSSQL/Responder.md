> To capture a hash with XP dirtree or another method where the user authenticates and we capture a hash:

```
sudo responder -I tun0 -A
```

Make sure to run -A for analyze mode to avoid spoofing which is prohibited in the OSEP exam.