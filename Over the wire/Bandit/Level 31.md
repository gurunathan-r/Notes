
```
ssh bandit30@bandit.labs.overthewire.org -p 2220
```

After logging in to the server we create a working directory in `/tmp` and clone the git repo.  
The password is the same as the one used to login to this level.

```shell
bandit30@bandit:~$ mkdir /tmp/bandit30
bandit30@bandit:~$ cd /tmp/bandit30

bandit30@bandit:/tmp/bandit30$ git clone ssh://bandit30-git@localhost/home/bandit30-git/repo
Cloning into 'repo'...

bandit30-git@localhost's password:
remote: Counting objects: 4, done.
remote: Total 4 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (4/4), done.
```

First we change directory into the repo and check the `README.md` file

```shell
bandit30@bandit:/tmp/bandit30$ cd repo
bandit30@bandit:/tmp/bandit30/repo$ cat README.md
just an epmty file... muahaha

```

Nothing of interest in the `README.md` file.  
Next check the commit logs.

```shell
bandit30@bandit:/tmp/bandit30/repo$ git log
commit 3aefa229469b7ba1cc08203e5d8fa299354c496b
Author: Ben Dover <noone@overthewire.org>
Date:   Thu May 7 20:14:54 2020 +0200

    initial commit of README.md
```

The only commit is the initial commit which means the file was never changed after first commit.  
Next on to checking for branches.

```shell
bandit30@bandit:/tmp/bandit30/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```

No other branches locally or remote. Another dead end. Next I began looking at the `.git` directory

```shell
bandit30@bandit:/tmp/bandit30/repo$ cd .git
bandit30@bandit:/tmp/bandit30/repo/.git$ ls
branches  config  description  HEAD  hooks  index  info  logs  objects  packed-refs  refs
```

I started checking the files in .git and `packed-refs` contained something of interest.

```shell
bandit30@bandit:/tmp/bandit30/repo/.git$ cat packed-refs
# pack-refs with: peeled fully-peeled
3aefa229469b7ba1cc08203e5d8fa299354c496b refs/remotes/origin/master
f17132340e8ee6c159e0a4a6bc6f80e1da3b1aea refs/tags/secret
```

We can see a `secret` tag listed in the `packed-refs`. Using the `git tag` command we can list all tags.

```shell
bandit30@bandit:/tmp/working_dir/repo$ git tag
secret
```