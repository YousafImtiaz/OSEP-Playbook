> We can ssh to move laterally to another user if we are on a compromised machine. Make sure the check the known hosts file to get a hint on where you could move to:

```
ssh <user>@<domain>@<hostname>.<domain>
```

> If we have an id_rsa file we can login from kali:

```
ssh -i id_rsa <user>@<domain>
```

We could also try logging in from the compromised machine using the id_rsa file.