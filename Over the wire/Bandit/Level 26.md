Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not **/bin/bash**, but something else. Find out what it is, how it works and how to break out of it.

```
bandit25@melinda:~$ ls -a
.   .bandit24.password  .bashrc  .profile
..  .bash_logout        .pin     bandit26.sshkey
bandit25@melinda:~$ cat /etc/passwd | grep bandit26 
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
bandit25@melinda:~$ cat /usr/bin/showtext 
#!/bin/sh

more ~/text.txt
exit 0
```

Before we try to SSH into bandit26, shrink the Console down to only 5 lines and run the `SSH` command.

```
bandit25@melinda:~$ ssh -i bandit26.sshkey bandit26@localhost
```

Once the command is ran, press V and it should take you to VIM, then type:

```
:r /etc/bandit_pass/bandit26
```

Press `Enter`, and you should get the password!

```
5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z
```
