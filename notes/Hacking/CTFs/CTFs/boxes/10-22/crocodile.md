# {{10.129.238.67}}
## Enumeration
#### [[nmap]]
-`21/tcp open  ftp`
-`80/tcp open  http`

## Services
- http service looks standard
- ftp service has users/passwords open to anonymous user

## Exploitation
- used [[ftp]] to connect and retrive files of users
- used [[gobuster]] to find a dashbord directory, which used a user/passwd
