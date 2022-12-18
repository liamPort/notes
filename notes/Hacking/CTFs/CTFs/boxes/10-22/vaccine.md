# {{10.129.82.194}}
## Enumeration
#### [[nmap]]
-`21/tcp open  ftp`
-`22/tcp open  ssh`
-`80/tcp open  http`
##### notes
- can transfer files + get shell
- most likely http vector attack

#### http
##### notes
- login in page, no info
- go buster has nothing, ###/server-status

#### ftp#
##### notes
- Anonymous user was configured, got access to backup.zip 


## stage 2
- zip file was password protected, so i used [[zip2john]] to crack the password
- we put the hash output into a txt, and used [[john the ripper]] to crack
- then we opened the zip, and found a php file will a username and pass, however it did not work when used.

## stage 2
- the password was hashed, so we used [[hashid]]
- this returned a bunch of hashes however md5 was a match with the php
- i used [[hashcat]] to crack the pass 
- `hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt`
- which gave me `qwerty789` as admin pass

## stage 3
- we can now access the site, so we need to enumerate that as well
- its using php, and possible sql, so we are going to use [[sqlmap]]
- however since we needed to login we need to pass our cookies to sqlmap so its authenticated with the site
- `sqlmap --cookie="PHPSESSID=0982lleuajf5q8gunroqoinlg4" -u "http://10.129.82.194/dashboard.php?search="`
- this told us that the site is susceptible to [[sql injection]]
- we then run the same command, but with `--os-shell` payload, this will get us a shell through the the sql injection vun
- since its running a http server we can go and snoop in /var/www where it would be hosted
- in here we find `user=postgres password=P@s5w0rd!`
- user flag `ec9b13ca4d6229cd5cc1e09980965bf7`

## stage 4
- we can see we are part of the ssl-cert group[[ssl]]
- we can use `sudo -l` to find files we can run as root
- we found that we can run vi as sudo when we open a specific file
- using https://gtfobins.github.io/gtfobins/vi/#sudo, we can find how to get Privilege Escalation
- root flag `dd6e058e814260bc70e9bbdef2715849`