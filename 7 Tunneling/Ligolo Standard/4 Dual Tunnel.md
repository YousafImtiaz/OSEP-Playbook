If we have another internal IP Address on a compromised machine we can run agent.exe on it and establish a dual tunnel.

> First we add a listener on Ligolo:

```
listener_add --addr 0.0.0.0:443 --to 127.0.0.1:11601
```

> Now we run the agent.exe and target the internal IP Address of the original tunnel machine:

```
.\agent.exe --connect <ip>:443 -ignore-cert
```

On Ligolo we can select the session then autoroute again once the agent connects.