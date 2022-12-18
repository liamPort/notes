# {{10.129.149.59}}
## Enumeration
#### [[nmap]]
-`135/tcp  open  msrpc`
-`139/tcp  open  netbios-ssn`
-`445/tcp  open  microsoft-ds`
-`1433/tcp open  ms-sql-s`

 [[smbmap]]
ADMIN$                             | NO ACCESS       Remote Admin
backups                             | READ ONLY
C$                                      | NO ACCESS       Default share
IPC$                                   | READ ONLY       Remote IPC

#### notes
- [[smb]] server running
- [[netbios session service]] could allow for [[responder]] to be used, vuln service
- sql??

## Services
#### notes
- in the backups worshare, a DTSConfiguration file was found
- `Password=M3g4c0rp123;User ID=ARCHETYPE\sql_svc;`
- this is a config file for the [[Microsoft SQL Server]] on port 1433
- we can use a script from impacket collection to get a client with the server
- we use [[impacket-mssqlclient]] to connect to the server, and use -windows-auth to authenticate.
- finally we are in the mssql service, as archetype\sql_svc, with cmd
2

## Exploitation
- now i go about installing a reverse shell to make things easier, host a reverse shell file on a python http service
- use nc for windows to get reverse shell
- user flag `3e7b102e78218e935bf3f4951fec21a3`
- then downloaded winpeas to get win enum
- found file with `/user:administrator MEGACORP_4dm1n!!`
- used [[impacket-psexec]] to login to admin
- `b91ccec3305e98240082d4474b848528`

## post Exploitation
- we then searched for the flag and found it
