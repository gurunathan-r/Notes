
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

**NOTE:** To beat this level, you need to login twice: once to run the setuid command, and once to start a network daemon to which the setuid will connect.

**NOTE 2:** Try connecting to your own network daemon to see if it works as you think

```
bandit20@melinda:~$ ls -a
.  ..  .bash_logout  .bashrc  .profile  suconnect
bandit20@melinda:~$ nc -l 32123 < /etc/bandit_pass/bandit20
```

Once you got NC (Netcat) listening on port 32123 (or any port of your choosing), open another Terminal and login to Bandit20 via SSH.

```
bandit20@melinda:~$ ls -a
.  ..  .bash_logout  .bashrc  .profile  suconnect
bandit20@melinda:~$ ./suconnect 32123
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
Password matches, sending next password
```

Now if you look back at the first terminal you will see the password!

```
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```
