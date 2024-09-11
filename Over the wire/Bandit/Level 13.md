The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the data file using cp, and rename it using mv (read the manpages!)

```
bandit12@melinda:~$ ls -a
.  ..  .bash_logout  .bashrc  .profile  data.txt
bandit12@melinda:~$ mkdir /tmp/jhalon
bandit12@melinda:~$ xxd -r data.txt > /tmp/jhalon/file.bin
bandit12@melinda:~$ cd /tmp/jhalon
bandit12@melinda:/tmp/jhalon$ ls -a
.  ..  file.bin
bandit12@melinda:/tmp/jhalon$ file file.bin
file.bin: gzip compressed data, was "data2.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
bandit12@melinda:/tmp/jhalon$ zcat file.bin | file -
/dev/stdin: bzip2 compressed data, block size = 900k
bandit12@melinda:/tmp/jhalon$ zcat file.bin | bzcat | file -
/dev/stdin: gzip compressed data, was "data4.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
bandit12@melinda:/tmp/jhalon$ zcat file.bin | bzcat | zcat | file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@melinda:/tmp/jhalon$ zcat file.bin | bzcat | zcat | tar xO | file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@melinda:/tmp/jhalon$ zcat file.bin | bzcat | zcat | tar xO | tar xO | file -
/dev/stdin: bzip2 compressed data, block size = 900k
bandit12@melinda:/tmp/jhalon$ zcat file.bin | bzcat | zcat | tar xO | tar xO | bzcat | file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@melinda:/tmp/jhalon$ zcat file.bin | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | file -
/dev/stdin: gzip compressed data, was "data9.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
bandit12@melinda:/tmp/jhalon$ zcat file.bin | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | zcat | file -
/dev/stdin: ASCII text
bandit12@melinda:/tmp/jhalon$ zcat file.bin | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | zcat         
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

Please note! That we **MUST** remove the created directory after we are done. So we do the following…

```
bandit12@melinda:/tmp/jhalon$ cd ..
bandit12@melinda:/tmp$ rm -rf jhalon
bandit12@melinda:/tmp$ reset
```
