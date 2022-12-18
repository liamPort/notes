in the code 
```
uName = getRequestString("username");  
uPass = getRequestString("userpassword");  
  
sql = 'SELECT * FROM Users WHERE Name ="' + uName + '" AND Pass ="' + uPass + '"'
```
if for the username we input
- admin'#
the rest of the code will be commented, so the check will not be complete and we can login without password