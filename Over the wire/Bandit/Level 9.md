New technical commands are to be learnt

grep command :
1) so the grep command in linux is a powerful tool used to search and manipulate the patterns in text 
2) so the grep command is known for its efficiency and versatility in handling text data
3) syntax:
```
4) grep [options] pattern [files]
```


the options available in this grep command:

 -c        prints only a count of lines match a certain pattern
 -h        displays matched lines but not file name
 -i          ignores case for matching
 -l          displays list of a filenames only
 -n         displays the matched lines and their line numbers
 -v          prints out all the lines that do not matches the pattern
 -w         match a whole word
 -o          prints the matched parts of a matching line ,with each such part on a seperate output line
 -A n        prints searched line and n lines after result
 -B n        prints searched line and n lines before the result
 -C n        prints searched line and n lines after before result 



sort command :
SORT command is used to sort a file, arranging the records in a particular order.

The sort command follows these features as stated below:****  

1. Lines starting with a number will appear before lines starting with a letter.
2. Lines starting with a letter that appears earlier in the alphabet will appear before lines starting with a letter that appears later in the alphabet.
3. Lines starting with a uppercase letter will appear before lines starting with the same letter in lowercase.

options available in the grep command :

-o    -specifies an output for the sorted data
-r     -sorts data in reverse order
-n     -sorts a file numerically
-nr    -sorts numeric data in reverse order
-k     -sorts a table based on a specific column number 
-c      -cheks if the file is already sorted and reports
-u      -sorts and removes duplictae lines,provideing a unique sorted list
-M       -sorts by month names



uniq command:
  The uniq command in Linux is a command-line utility that reports or filters out the repeated lines in a file. In simple words, uniq is the tool that helps to detect the adjacent duplicate lines and also deletes the duplicate lines.


so i just logged in bandit8 using -ssh ,then i went on using the ls and used 
```
uniq -u data.txt
```

then i got a list of  words i was just expecting a one line of password but got a list of keys 

then i used  
```
 bandit8@bandit:~$ uniq -d data .txt
fWBv5AzQI14holge9okDaOvrgL7NGNTr
zOTIYMCpuvJ0DZGzoEwqIYc19SkIVQdl
tUlwNyLyJjRiFaj4n0oN5cvoUlJKpW8m
swXvCokPAhVazCnl9rPeLXWYHIC5yj8h
PQ0a8vewEyqcaKm7P21uKO88lpXupIMi
bJDV41So5UyGPR98w9x5pX6nqWsOU2ra
TOWEeiT4P5TcGnZ2pyG63NKEvTm0MdPg
```

then i tried used  
```
sort -u data.txt
```
even there no luck
then i tried combining sort and uniq
```
sort data.txt uniq -u
```



![[Pasted Level 9.png]]

then got the code:
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
