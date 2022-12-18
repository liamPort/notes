# {{10.129.108.105}}
## Enumeration
#### [[nmap]]
-`22/tcp open  ssh`
-`80/tcp open  http`

#### notes
- domain: megacorp.com

## Services
#### notes
- php, can access tables of conten including id, and users
- using [[burpe suite]] to modifiy requests, and change cookies sent to website
- admin id = 34322
- able to upload files, so uploaded php revese shell
- then went to url with revese shell on
- user robert flag:f2c74ee8db7983851ab2a96a44eb7981
- and robert group
- pass found:M3g4C0rpUs3r!
- root flag:af13b0bee69f8a877c3faf667f7beacf
## Exploitation
-the http service is using [[Name-Based Virtual Hosting]] meaning when we got redirected the domain is hosting mutiple sites, and needs a host(the ip of the last host) to give us the right web page
-for this we added the {ip domain} to /etc/hosts so when we send the http request the ip the domain will also be sent
### [[File Inclusion Vulnerability]]
- the php allowed us to use this exploit to view over files on the server through the php request in the url `http://unika.htb/index.php?page=file`
- it also allows us to use Remote [[file inclusion vulnerability]], so we can get files off the network, and request files from other machines
- this allows us for the machine to make a query which is invalid because this most windows machines uses [[Windows New Technology LAN Manager]]  we can use [[responder]] to get a hash of the machines password
### finnally
Finally we used [[john the ripper]] to crack the hash and used [[evil-winrm]] to get a shell to the [[windows remote managment]] service that was running, with the name and passwd given by john