I used the legacy version of BloodHound as I like the visual graph and its easier to see the attack paths.

> On kali:

```
sudo neo4j start
```

```
bloodhound-legacy
```

> On the target, download ShaprHound.ps1 (Older version) and then run:

```
Invoke-BloodHound -CollectionMethod All -outputdirectory <path>
```

> If it dosent work or takes too long then run an alternative:

```
Invoke-BloodHound -CollectionMethod 'Group,LocalAdmin,Session,Trusts'
```

Once we have imported our ZIP into BloodHound I like to run these queries to find any quick wins:

> Display all computers in the domain:

```
MATCH (m:Computer) RETURN m
```

> Display all users in the domain:

```
MATCH (m:User) RETURN m
```

> Display any active sessions users have on computers (cached credentials):

```
MATCH p = (c:Computer)-[:HasSession]->(m:User) RETURN p
```

Here you want to look at what users you have compromised and what groups they are a part of and what permissions the users and machines have over others in the domain.

> If we have an SID in bloodhound we can try and see what it is in PS using PowerView:

```
convertfrom-sid <sid>
```

Make sure to right click on a target machine and use "shortest path from here" if you cant find a path to compromise in BloodHound. whenever you compromise a user or machine mark it as owned in BloodHound as well so you can query "shortest path from owned".






