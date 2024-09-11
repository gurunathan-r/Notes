There are 2 files in the homedirectory: **passwords.old** and **passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old** and **passwords.new**

**NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19**

```
bandit17@melinda:~$ ls -a
.   .bandit16.password  .bashrc   .ssh                    passwords.new
..  .bash_logout        .profile  .ssl-cert-snakeoil.key  passwords.old
bandit17@melinda:~$ diff passwords.new passwords.old
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
---
> BS8bqB1kqkinKJjuxL6k072Qq9NRwQpR
```


 
 `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd` is our password as `diff` shows what needs to be changed to equal the second file. `<` means first file (so **passwords.new**) and `>` means second file (so **passwords.old**)