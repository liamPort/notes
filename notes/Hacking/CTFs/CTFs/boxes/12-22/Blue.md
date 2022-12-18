# {{10.10.10.40}}
#aws #asw_s3 #shellscript #php #http
## Enumeration
#### [[nmap]]
-`22/tcp open  ssh`
-`135/tcp   open  msrpc`
-`139/tcp   open  netbios-ssn
-`445/tcp   open  microsoft-ds
-`49152/tcp open  unknown
-`49153/tcp open  unknown
-`49154/tcp open  unknown
-`49155/tcp open  unknown
-`49156/tcp open  unknown
-`49157/tcp open  unknown


#### notes
-port 445
	microsoft-ds is a [[smb]] server
-port 139 netbios
	could use [[responder]] as device makes use of [[Windows New Technology LAN Manager]]

## Services
- php running on main domain
- [[aws s3]]
## Exploitation
- used [[awscli]] to upload malicious files to the webserver
- being a php command execution file
- we also uploaded a [[shell script]] file, containg a reverse shell script
## post Exploitation
- we then searched for the flag and found it
