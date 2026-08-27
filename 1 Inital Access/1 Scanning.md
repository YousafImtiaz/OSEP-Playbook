> I used my tool here: https://github.com/YousafImtiaz/Nportsc/tree/main

```
sudo python3 /home/kali/nportsc.py <ip> --tcp T4
```

> UDP (most likely not needed but added it here anyway as its always nice to check):

```
sudo python3 /home/kali/nportsc.py <ip> --udp T4
```

When looking at the output of nmap, if there is a FQDN make sure to add it to /etc/hosts and browse to the webpage using the domain name.