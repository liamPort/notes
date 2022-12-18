# {{10.129.133.6}}
## Enumeration
#### [[nmap]]
-`135/tcp open  msrpc`
-`139/tcp open  netbios-ssn`
-`445/tcp open  microsoft-ds` [[smb]]

#### [[smbmap]]
$ smbmap -H 10.129.133.6 -u User     
[+] Guest session       IP: 10.129.133.6:445    Name: 10.129.133.6                                      
        Disk                                                    Permissions     Comment
        ----                                                    -----------     -------
        ADMIN$                                                  NO ACCESS       Remote Admin
        C$                                                      NO ACCESS       Default share
        IPC$                                                    READ ONLY       Remote IPC
        WorkShares                                              READ, WRITE                     

**Therfore we can see the WorkShares share has permissions so we can use it**
## Services
- [[smb]] port 445
## Exploitation
- Share on smb was open with no permissinons needed
- used [[smbclient]] to connect to sever and get flag
## post Exploitation
- used get to download the file# {{ip addr}}
