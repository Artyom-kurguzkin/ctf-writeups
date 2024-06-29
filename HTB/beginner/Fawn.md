
## scan

```bash
$ nmap -sS -A <targetIP>
```

```
PORT   STATE SERVICE VERSION  
21/tcp open  ftp     vsftpd 3.0.3  
| ftp-syst:    
|   STAT:    
| FTP server status:  
|      Connected to ::ffff:10.10.14.163  
|      Logged in as ftp  
|      TYPE: ASCII  
|      No session bandwidth limit  
|      Session timeout in seconds is 300  
|      Control connection is plain text  
|      Data connections will be plain text  
|      At session startup, client count was 1  
|      vsFTPd 3.0.3 - secure, fast, stable  
|_End of status  
| ftp-anon: Anonymous FTP login allowed (FTP code 230)  
|_-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt
```

* here, we can try to log in without user credentials because Anonymous FTP login allowed.

<br>

## Access through ftp

```bash
$ nala install ftp
$ ftp anonymous@<targetIP>
ftp> ENTER
ftp> dir
ftp> get flag.txt
ftp> exit
$ cat flag.txt
```

