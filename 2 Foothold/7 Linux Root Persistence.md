> Once we have root we can add a new user to the machine so we can login via SSH from kali:

```
adduser <username>
```

> Here we can leave everything blank and just press ENTER for the prompts. Once we have done that we can add a line in the `/etc/sudoers` file to allow ALL on the new user so we can become root once we login:

```
nano /etc/sudoers
```

```
<username> ALL=(ALL:ALL) ALL
```

Now just login with SSH and then run `sudo /bin/bash` to become root.
