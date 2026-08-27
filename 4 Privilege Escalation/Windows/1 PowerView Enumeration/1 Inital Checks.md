> **Check for Unconstrained Delegation:**

```
Get-DomainComputer -Unconstrained
```

> **Check for Constrained Delegation:**

```
Get-DomainUser -TrustedToAuth
```

> **Check SPNS for Kerberoasting:**

```
Get-NetUser -SPN | Select-Object name, enabled, passwordlastset, lastlogon, serviceprincipalname
```

> **Check for SPNs with internal webservers:**

```
Get-NetUser -SPN -Domain <domain> | Select-Object samaccountname, serviceprincipalname
```
