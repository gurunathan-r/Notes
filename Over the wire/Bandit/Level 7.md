so this time they  gave three hint that the file is a owned by bandit7 and group bandit6 and size of 33 bytes so 
1) i went in and typed ls in home directory to find nothing in there
2) then i typed ls -a to see hidden files there then i used cat command to open them all but it was all some commands and code which lead to nothing
3) then i though of using find command  then i used -user and -group for the given hint and -size and went in 
4) then i found a list of permisstion denied error in it 
5) then i tried some other commands and it failed too then went online to see how to access the files then found out that we should copy and move the file to some other directory and then access it 
```
   find -user bandit7 -group bandit6 -size 33c 2>/dev/null/var/lib/dpkg/info/bandit7.password
```
6 then wen to that directory and accessed it with cat command
![[Pasted Level 7.png]]


code:
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
