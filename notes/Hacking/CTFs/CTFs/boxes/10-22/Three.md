# {{10.129.90.81}}
#aws #asw_s3 #shellscript #php #http
## Enumeration
#### [[nmap]]
-`22/tcp open  ssh`
-`80/tcp open  http`

#### [[gobuster]]
- no directories found
- using vhost, subdomain s3.thetoppers.htb was found

#### other
domains on 10.129.90.81: 
- thetoppers.htb
- domain:s3.thetoppers.htb

## Services
- php running on main domain
- [[aws s3]]
## Exploitation
- used [[awscli]] to upload malicious files to the webserver
- being a php command execution file
- we also uploaded a [[shell script]] file, containg a reverse shell script
## post Exploitation
- we then searched for the flag and found it
