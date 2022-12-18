## Description
Responder listens on the wire for NetBIOS Name Service (NetBIOS) and Link-Local Multicast Name Resolution (LLMNR) broadcast and multicast requests for hostnames from other machines in the local subnet.
In short, it is common for a windows machines that are unable to resolve a hostname through DNS or their own local files, the machine will ask its subnet if any of the machines are the one its looking for. responder steps in and says yes, the tricked machine tries to authenticate, the hash recived by responder can then be cracked offline, by [[john the ripper]] or other utilities 


## usages
-`-I`This is used to specify what socket to serve to
