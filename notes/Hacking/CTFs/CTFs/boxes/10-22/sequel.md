# {{10.129.125.7}}
#mysql #mariaDB
## Enumeration
#### [[nmap]]
-`3306/tcp open  mysql`

## Services
- [[MariaDB]] port 445, similar to [[mysql]]
## Exploitation
- used defult root password, used [[mysql]] to login
## post Exploitation
- flag was in the htb database, config table
- used [[MariaDB]] commands to navagate database
