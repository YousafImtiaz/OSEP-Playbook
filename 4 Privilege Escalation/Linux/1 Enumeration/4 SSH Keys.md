If you have an SSH key then try to run it for a different user once you have the list of users on the system. Also look for .ssh when you run `ls -la` in users home folders.

> We can use this command to find ssh keys:

```
find / -name id_rsa 2> /dev/null
```

> Also look for controlmaster for ssh hijacking:

```
/home/<user>/.ssh/controlmaster$ 
```

> We may find an entry here if we check after a 1 minute interval. If there is an entry we can SSH from here to another users session:

```
ssh <user>@<hostname>
```

> Check where keys might be used:

```
cat /etc/passwd
cat known_hosts
tail .bash_history
cat /etc/ansible/hosts
```

> If we find a hostname we can use the following to determine the IP Address:

```
host <hostname>
```

> Once we have passphrase from id_rsa we can log into machine from our original target:

```
ssh -i id_rsa <user>@<target_hostname>
```

