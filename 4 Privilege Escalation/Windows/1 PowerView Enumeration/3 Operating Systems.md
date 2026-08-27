> Get information about computer objects in the domain:

```
Get-NetComputer

Get-DomainComputer -Domain <domain>
```

> Get a clean list of all computers and associated DNS hostname and OS version:

```
Get-NetComputer | select dnshostname,operatingsystem,operatingsystemversion
```
