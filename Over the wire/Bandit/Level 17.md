The credentials for the next level can be retrieved by submitting the password of the current level to a **port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

```
bandit16@melinda:~$ nmap -p 31000-32000 -sV  localhost

Starting Nmap 6.40 ( http://nmap.org ) at 2016-09-09 01:39 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00050s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE VERSION
31046/tcp open  echo
31518/tcp open  msdtc   Microsoft Distributed Transaction Coordinator (error)
31691/tcp open  echo
31790/tcp open  msdtc   Microsoft Distributed Transaction Coordinator (error)
31960/tcp open  echo
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 41.34 seconds

bandit16@melinda:~$ echo cluFn7wTiGryunymYOu4RcffSxQluehd | openssl s_client -quiet -connect localhost:31518
depth=0 CN = li190-250.members.linode.com
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = li190-250.members.linode.com
verify return:1
cluFn7wTiGryunymYOu4RcffSxQluehd

bandit16@melinda:~$ echo cluFn7wTiGryunymYOu4RcffSxQluehd |openssl s_client -quiet -connect localhost:31790
depth=0 CN = li190-250.members.linode.com
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = li190-250.members.linode.com
verify return:1
Correct!
-----BEGIN RSA PRIVATE KEY-----
[redacted]
-----END RSA PRIVATE KEY-----
```

Great! So let’s copy the RSA Key (Don’t forget to get the Header and Footer) and create a new file in a tmp directory.

```
bandit16@melinda:~$ mkdir /tmp/jhalon
bandit16@melinda:~$ cd /tmp/jhalon
bandit16@melinda:/tmp/jhalon$ nano sshkey.private
bandit16@melinda:/tmp/jhalon$ chmod 600 sshkey.private
bandit16@melinda:/tmp/jhalon$ ssh -i ./sshkey.private bandit17@localhost
```
