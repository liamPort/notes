# {{10.129.83.251}}
## Enumeration
#### [[nmap]]
-`6379/tcp open  redis`

## Services
- [[redis]] port 6379
## Exploitation
- database was open, with no premissions in place
## post Exploitation
- used [[redis-cli]] to gain access to database and retrive flag
