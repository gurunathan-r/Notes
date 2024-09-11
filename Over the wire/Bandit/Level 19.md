

```
$ ssh bandit19@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames
bandit19@bandit.labs.overthewire.org's password:
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```


by using id and going through al the files e cn find the key in bandit 20 file
```
bandit19@bandit:~$ ls
bandit20-do
bandit19@bandit:~$ ls -al ./bandit20-do
-rwsr-x--- 1 bandit20 bandit19 7296 Oct 16 14:00 ./bandit20-do
bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id
bandit19@bandit:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
bandit19@bandit:~$ ls /etc/bandit_pass/bandit*
/etc/bandit_pass/bandit0   /etc/bandit_pass/bandit17  /etc/bandit_pass/bandit25  /etc/bandit_pass/bandit33
/etc/bandit_pass/bandit1   /etc/bandit_pass/bandit18  /etc/bandit_pass/bandit26  /etc/bandit_pass/bandit4
/etc/bandit_pass/bandit10  /etc/bandit_pass/bandit19  /etc/bandit_pass/bandit27  /etc/bandit_pass/bandit5
/etc/bandit_pass/bandit11  /etc/bandit_pass/bandit2   /etc/bandit_pass/bandit28  /etc/bandit_pass/bandit6
/etc/bandit_pass/bandit12  /etc/bandit_pass/bandit20  /etc/bandit_pass/bandit29  /etc/bandit_pass/bandit7
/etc/bandit_pass/bandit13  /etc/bandit_pass/bandit21  /etc/bandit_pass/bandit3   /etc/bandit_pass/bandit8
/etc/bandit_pass/bandit14  /etc/bandit_pass/bandit22  /etc/bandit_pass/bandit30  /etc/bandit_pass/bandit9
/etc/bandit_pass/bandit15  /etc/bandit_pass/bandit23  /etc/bandit_pass/bandit31  /etc/bandit_pass/bandit16  /etc/bandit_pass/bandit24  /etc/bandit_pass/bandit32
bandit19@bandit:~$ ls /etc/bandit_pass/bandit20
/etc/bandit_pass/bandit20
bandit19@bandit:~$ cat /etc/bandit_pass/bandit20
cat: /etc/bandit_pass/bandit20: Permission denied
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```


key :
GbKksEFF4yrVs6il55v6gwY5aVje5f0j