> **Check if Microsoft Defender or Antivirus is enabled:**

```
Get-Process | Where-Object {$_.ProcessName -match "MsMpEng|ClamAV|Avira"} | Format-Table ProcessName
```

```
Get-MpComputerStatus | Select-Object AntivirusEnabled, RealTimeProtectionEnabled, AMServiceVersion
```

If we get ProcessName then it is running. The above command also checks if real time protection is on.

> **Check if LSA Protection is enabled in PS:**

```
Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Control\Lsa -Name "RunAsPPL"
```

If it returns 1 then it is enabled.

> **Check if AMSI is enabled:**

```
"Invoke-Expression 'amsiutils'"
```

> **Check if Constrained Language Mode is enabled:**

```
$ExecutionContext.SessionState.LanguageMode
```

> **Check if AppLocker is enabled:**

> This will show the rules in place for Application Whitelisting:

```
Get-AppLockerPolicy -Effective | Select-Object -ExpandProperty RuleCollections
```

> This will check for running process of Application Identity. If it is running then the policies are active:

```
Get-Service AppIDSvc | Select-Object Name, Status, StartType
```

> Check AppLocker rules:

```
Get-ChildItem -Path HKLM:\SOFTWARE\Policies\Microsoft\Windows\SrpV2\Exe
```
