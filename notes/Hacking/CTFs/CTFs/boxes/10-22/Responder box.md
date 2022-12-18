# {{10.129.185.146}}
#php #http #wsman 
## Enumeration
#### [[nmap]]
-`80/tcp open  http`
-`5985/tcp open  wsman`
#### wappalyser
-we can see [[php]] is running
## Services
- http redirects to a domain with no service
- wsman or [[windows remote managment]] on port 5985 is a windows managment system
- used php to load page, so [[File Inclusion Vulnerability]] could be explotible
## Exploitation
-the http service is using [[Name-Based Virtual Hosting]] meaning when we got redirected the domain is hosting mutiple sites, and needs a host(the ip of the last host) to give us the right web page
-for this we added the {ip domain} to /etc/hosts so when we send the http request the ip the domain will also be sent
### [[File Inclusion Vulnerability]]
- the php allowed us to use this exploit to view over files on the server through the php request in the url `http://unika.htb/index.php?page=file`
- it also allows us to use Remote [[file inclusion vulnerability]], so we can get files off the network, and request files from other machines
- this allows us for the machine to make a query which is invalid because this most windows machines uses [[Windows New Technology LAN Manager]]  we can use [[responder]] to get a hash of the machines password
### finnally
Finally we used [[john the ripper]] to crack the hash and used [[evil-winrm]] to get a shell to the [[windows remote managment]] service that was running, with the name and passwd given by john