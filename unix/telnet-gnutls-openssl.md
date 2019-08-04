_Written by: Reza Shams Amiri_
# telnet gnutls openssl

Several ways to test a web site:

1. **telnet**:
   ``` sh
   telnet localhost 4200
   ```
   After you are connect, enter your command and press <kbd>ENTER</kbd> **twice**. 
   See more info this [page][HBNID2H].
   
   _telnet can be used to connect to an https site, but you can't issue commands to that site use `openssl`, `gnutls-cli` instead_{.note}
3. **openssl**:
   ``` sh
   openssl s_client -connect localhost:4200
   ```
   After you are connect, enter your command and press <kbd>ENTER</kbd> **twice**. 
4. **nc**:
   ``` sh
   nc -vz localhost 4200
   ```
6. **gnutls-cli**:
   ``` sh
   gnutls-cli imap.gmail.com:993
   gnutls-cli localhost:4200 --tofu       # use tofu for accepting self signed certificate
   gnutls-cli -d 1 localhost:4200 --tofu  # Specify log level
   ```
   After you are connect, enter your command and press <kbd>ENTER</kbd> **twice**. ex:
   ``` sh
   GET / HTTP/1.1 
   
   ```


* * *
Creation date: _2019-08-04_

[HBNID2H]: http://blog.nullspace.io/day-208.html