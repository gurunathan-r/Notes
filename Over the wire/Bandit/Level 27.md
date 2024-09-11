Login to the server using the steps from the previous level to escape the shell. [Bandit level 25 -> 26](https://github.com/mmacdonnacha/Overthewire.org-Solutions/blob/main/bandit/bandit25-26/README.md).

The first thing to do is check the home directory.

```shell
bandit26@bandit:~$ ls -al
total 36
drwxr-xr-x  3 root     root     4096 May  7  2020 .
drwxr-xr-x 41 root     root     4096 May  7  2020 ..
-rwsr-x---  1 bandit27 bandit26 7296 May  7  2020 bandit27-do
-rw-r--r--  1 root     root      220 May 15  2017 .bash_logout
-rw-r--r--  1 root     root     3526 May 15  2017 .bashrc
-rw-r--r--  1 root     root      675 May 15  2017 .profile
drwxr-xr-x  2 root     root     4096 May  7  2020 .ssh
-rw-r-----  1 bandit26 bandit26  258 May  7  2020 text.txt
```

There is a `bandit27-do` file and it has the setuid bit set.  
`-rwsr-x--- 1 bandit27 bandit26 7296 May 7 2020 bandit27-do`

This means we can use `bandit27-do` to run files with elevated priviledges.

```shell
bandit26@bandit:~$ ./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id

bandit26@bandit:~$ ./bandit27-do id
uid=11026(bandit26) gid=11026(bandit26) euid=11027(bandit27) groups=11026(bandit26)
```

`bandit27-do` takes another command as its argument and then runs that command as user bandit27.  
When running `bandit27-do id` we can see the euid is bandit27.
