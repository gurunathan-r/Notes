

so for this level its about the ssh command in linux . SSH is like a secure encrypted way of communication between two far away computers or a server .. 

To access it the command line for syntax is :

```
ssh [username]@[hostname or IP address]
```

so there are somethings to be noted to perform SSH

1)The remote server or pc should be on and to be connected to a network for access
2)The username and password to access the correct server 
3)Permission to access the server 
4)permission from the firewall (port 22 usually) to allow SSH traffic

### ****Installing it on Both Client and Server****

For Debian/Ubuntu-based Systems, open the terminal and run:

```
sudo apt install openssh-client openssh-server
```

A sample code for this is:

```
ssh jayesh@10.143.90.2
```

so after that i went to study all The available options in ssh so i used geeks for geeks website for reference and i found most of the commands hard to understand so used copilot to understand better .

Some options in ssh.

- -1       forces ssh to portocol 1
- -2        forces ssh to portocol 2
- -4        used to allow ipv4
- -6         used to allow ipv6
- -A        enables Authentication agent connection forwarding 
- -a         disables Authentication agent connection forwarding 
- -C         compress all data for high latency devices for faster transfer
- -c          used to specify the chiper code used for encryption
- -f           used to automate a work on remote server and detach from the pc  without waiting for the machine to complete the task
- -`-g`        option in the `ssh` command allows **remote hosts** to connect to **local forwarded ports**. used along with -L for local forwarded ports
- -n        same as -f but it wont read any stdin or standard input from the user during execution
- -p         Port to connect to on the remote host.
- -q         Quite mode skips all errors 
- -V          displays the version number
- -v`: This level informs you about what is happening mostly on your end.
- `-vv`: Provides low-level information from both ends.
- `-vvv`: Gives you detailed information about everything from both ends.
- -x         Enables  X11 forwarding allows to run graphical applications


So SSH is more secure than a command telnet so basically there are three types of encryption

1)Symmetric Encryption :  
            This type of encrytion is a basic kinda encryption which encrypts the datas by a basic key and distributed among clients
2) Asymmetric Encryption:
             THis type of encription has two keys public and private keys public keys are given to the clients and private keys are kept in the clientmachine. A secure connection is established between the pcs using public and private key pair
3)Hashing:
               One-way hashing is an authentication technique which ensures that the received data is unaltered and comes from a genuine sender. A hash function is used to generate a hash code from the data. It is impossible to regenerate the data from the hash value. The hash value is calculated at the sender as well as the receiver’s end. If the hash values match, the data is authentic.

so by entering the command i finnaly madeit into the contest

![[Pasted Level 0.png]]

keywords:
	 AES    advanced encryption standard
	TCP      Transmission control protocol
	 IP         Internet protocol

reference:
[[[How do I use SSH to connect to a remote server in Linux | ssh Command - GeeksforGeeks](https://www.geeksforgeeks.org/ssh-command-in-linux-with-examples/)]]
