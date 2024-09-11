
```
ssh bandit28@bandit.labs.overthewire.org -p 2220
```

For this challenge we need to clone a git repository and search the repo for the password.  
First thing is to create a working directory to clone the repository into and then clone the repo.

```shell
bandit28@bandit:~$ mkdir /tmp/bandit28
bandit28@bandit:~$ cd /tmp/bandit28

bandit28@bandit:/tmp/bandit28$ git clone ssh://bandit28-git@localhost/home/bandit28-git/repo
Cloning into 'repo'...

bandit28-git@localhost's password:
remote: Counting objects: 9, done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0)
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.

bandit28@bandit:/tmp/bandit28$
```

Now that the repo has been cloned we can change into the repo directory and start inspecting.  
Using `git log` we can check the history of the repo.

```shell
bandit28@bandit:/tmp/bandit28$ ls
repo

bandit28@bandit:/tmp/bandit28$ cd repo/
bandit28@bandit:/tmp/bandit28/repo$ git log
commit edd935d60906b33f0619605abd1689808ccdd5ee
Author: Morla Porla <morla@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    fix info leak

commit c086d11a00c0648d095d04c089786efef5e01264
Author: Morla Porla <morla@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    add missing data

commit de2ebe2d5fd1598cd547f4d56247e053be3fdc38
Author: Ben Dover <noone@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    initial commit of README.md

bandit28@bandit:/tmp/bandit28/repo$
```

Git log shows 3 commits in the history.

- fix info leak
- add missing data
- initial commit of README.md

Currently the `README` file does not contain the password.

```
bandit28@bandit:/tmp/bandit28/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx

bandit28@bandit:/tmp/bandit28/repo$
```

By reading the commit descriptions we can assume the password was removed in the `fix info leak` commit. We need to see what was in the file in the other commits.

Using `git diff <commit id>` we can see what changes were made between the current commit and the commit id we enter.

We can use the commit id of the `add missing data` commit to see what was in the README before the info leak was fixed.