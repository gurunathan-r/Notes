
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

```
bandit21@melinda:~$ cd /etc/cron.d/
bandit21@melinda:/etc/cron.d$ ls -a
.                  cronjob_bandit24       natas25_cleanup   semtex0-ppc
..                 cronjob_bandit24_root  natas25_cleanup~  semtex5
.placeholder       leviathan5_cleanup     natas26_cleanup   sysstat
behemoth4_cleanup  manpage3_resetpw_job   natas27_cleanup   vortex0
cron-apt           melinda-stats          php5              vortex20
cronjob_bandit22   natas-session-toucher  semtex0-32
cronjob_bandit23   natas-stats            semtex0-64
bandit21@melinda:/etc/cron.d$ cat cronjob_bandit22
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@melinda:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@melinda:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
```

