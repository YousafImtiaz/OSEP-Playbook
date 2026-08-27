> If we find an ansible hosts file we can try to run commands on the target machine:

```
ansible <hostname>.<domain> -a "whoami" --become
```

If we get a response of root we can try and SSH to the machine or `su` to the user.