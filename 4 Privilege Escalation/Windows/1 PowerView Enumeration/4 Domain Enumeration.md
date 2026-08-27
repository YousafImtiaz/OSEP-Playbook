> Check for tickets and purge them if necessary before doing an attack:

```
klist
klist purge
```

> View information about DC's in the domain:

```
Get-ForestDomain
```

> Check what domain a computer is in if there are multiple domains:

```
Get-DomainComputer -Identity <hostname>
```

> Enumerate Domain Trusts (also do recursive search to find an child domains):

```
Get-ForestDomain -Forest <domain>
```

> Enumerate Groups in the domain:

```
Get-DomainGroup -Domain <domain> | select SamAccountName
```

> If we find an interesting group we can see what users are in it:

```
Get-DomainGroupMember -Domain <domain> -Identity "<group>"

Get-DomainUser -Domain <domain>
```

> Check which machines are part of the domain for lateral movement:

```
Get-DomainComputer -Domain <domain> -Properties DnsHostName | sort -Property DnsHostName
```
