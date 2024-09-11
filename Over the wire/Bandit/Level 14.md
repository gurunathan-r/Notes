The password for the next level is stored in **/etc/bandit_pass/bandit14** and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

```
bandit13@melinda:~$ ls -a 
.  ..  .bash_logout  .bashrc  .profile  sshkey.private
bandit13@melinda:~$ ssh -i sshkey.private bandit14@localhost
Are you sure you want to continue connecting (yes/no)? yes
```

Great! We are inside Bandit14! So now let’s get the password from **/etc/bandit_pass/bandit14**

```
bandit14@melinda:~$ cat /etc/bandit_pass/bandit14
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```