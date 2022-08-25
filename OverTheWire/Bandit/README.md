<div align="justify">
  
# **BANDIT**

## **Bandit Level 0**
### **Level Goal**

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

### **Commands you may need to solve this level** ###
ssh

### **Solution**
- Use the command ssh
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
- It will ask you for the password, type this
```
bandit0
```
  
---
  
## **Bandit Level 0 → Level 1**
### **Level Goal**

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

### **Commands you may need to solve this level** ###
ls, cd, cat, file, du, find

### **Solution**
- Type ls command to view the the content
```
ls
```
- Use cat command to view the content file name "readme"
```
cat readme
```
### **Flag/Password**
```
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
  
---
  
## **Bandit Level 1 → Level 2**
### **Level Goal**

The password for the next level is stored in a file called - located in the home directory

### **Commands you may need to solve this level** ###
ls, cd, cat, file, du, find

### **Solution**
- Type ls command to view the the content
```
ls
```
- Use the cat command followed by ./ (because the file name starts with "-") to view the content
```
cat ./-
```
### **Flag/Password**
```
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
  
---

## **Bandit Level 2 → Level 3**
### **Level Goal**

The password for the next level is stored in a file called spaces in this filename located in the home directory

### **Commands you may need to solve this level** ###
ls, cd, cat, file, du, find

### **Solution**
- Type ls command to view the the content
```
ls
```
- Type cat command and the filename, but simply use cat command and just press tab key
```
cat spaces\ in\ this\ filename
```
### **Flag/Password**
```
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

---
  
## **Bandit Level 3 → Level 4**
### **Level Goal**

The password for the next level is stored in a hidden file in the inhere directory.

### **Commands you may need to solve this level** ###
ls, cd, cat, file, du, find

### **Solution**
- Type cd command with the directory inhere
```
cd inhere
```
- Type ls -a to list all hiddden files
```
ls -a
```
- Type cat command followed by the hidden file we saw
```
cat .hidden
```
### **Flag/Password**
```
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

---

## **Bandit Level 4 → Level 5**
### **Level Goal**

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

### **Commands you may need to solve this level** ###
ls, cd, cat, file, du, find

### **Solution**
- Type cd command with the directory inhere
```
cd inhere
```
- Type file command followed by the ./* (to list the file types of all files)
```
file ./*
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/149615678-c76ec901-6c97-48d3-b229-ef985fdf43c4.png">
</p>
  
- Now, we can see that there is only one file type that is in ASCII text, let's find out
```
cat ./-file07
```
### **Flag/Password**
```
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```
  
---
  
## **Bandit Level 5 → Level 6**
### **Level Goal**

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

### **Commands you may need to solve this level** ###
ls, cd, cat, file, du, find

### **Solution**
- Type cd command with the directory inhere
```
cd inhere
```
- There is a lot of directories and it is time consuming if we check each directories and files, so we need to use find command followed with the argument -size to find the file that has 1033 bytes
```
find ./* -size 1033c
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/149616175-64bd70df-f66e-4cc7-ad19-625c8af1813c.png">
</p>
  
- Now, we can see that there is a file consist of 1033 bytes
```
cat ./maybehere07/.file2
```
### **Flag/Password**
```
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```
  
---
  
## **Bandit Level 6 → Level 7**
### **Level Goal**

The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size

### **Commands you may need to solve this level** ###
ls, cd, cat, file, du, find, grep

### **Solution**
- Type cd command and go to root directory
```
cd /
```
- As per instructions, we can use the find command and the arguments -group and -user
```
find / -user bandit7 -group bandit6
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/149616439-80414fea-8d1a-4238-9697-03312ce9d38c.png">
</p>
  
- Now, we can see that there is a one file that has granted permission. Check the size of that file using du command
```
du -b /var/lib/dpkg/info/bandit7.password
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/149616535-8a1596a2-1a85-4bdc-b8c6-68631b0148e5.png">
</p>
  
- Yes, it is 33 bytes. Use the cat command
```
cat /var/lib/dpkg/info/bandit7.password
```
### **Flag/Password**
```
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```
  
---
  
## **Bandit Level 7 → Level 8**
### **Level Goal**

The password for the next level is stored in the file data.txt next to the word millionth

### **Commands you may need to solve this level** ###
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### **Solution**
- Type ls command to list contents
```
ls
```
- Use cat command
```
cat data.txt
```
- We saw that data.txt file has a lot words and numbers and it is time consuming if we seacrh it one-by-one. To do this, type grep command to search for the word "millionth"
```
grep "millionth" data.txt
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/149616793-1b7a03d1-3c8b-4834-9dab-f3e6b5d10cca.png">
</p>
  
### **Flag/Password**
```
cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
  
---
  
## **Bandit Level 8 → Level 9**
### **Level Goal**

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

### **Commands you may need to solve this level** ###
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### **Solution**
- Use cat command
```
cat data.txt
```
- We saw that data.txt file has a lot words and numbers. Basically, we can use sort command and we can use piping method to uniq command to execute the two commands easily
```
sort data.txt | uniq -c
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/149617115-6ae855c1-3f6b-48bd-b022-f8b21583f0c3.png">
</p>
  
- Now, we can see that almost lines has 10 occurrences but there is one line that has occurs once only. Copy the line that has 1 before to it.

### **Flag/Password**
```
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
  
---
  
## **Bandit Level 9 → Level 10**
### **Level Goal**

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

### **Commands you may need to solve this level** ###
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### **Solution**
- Use cat command
```
cat data.txt
```
- We saw that data.txt file consist of binary or something. Type cat command and use piping method with strings method (to convert binary into ASCII characters) and grep
```
cat data.txt | strings | grep '='
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/149617255-967bbada-c3d0-4fc6-a890-fd20618d1970.png">
</p>

### **Flag/Password**
```
truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```
  
---
  
## **Bandit Level 10 → Level 11**
### **Level Goal**

The password for the next level is stored in the file data.txt, which contains base64 encoded data

### **Commands you may need to solve this level** ###
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### **Solution**
- Use cat command
```
cat data.txt
```
- We saw that data.txt file consist random strings. As per instructions, the file is encrypted using base64. We can pipe the base64 command followed by the -d (decode) argument
```
cat data.txt | base64 -d
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/149617403-19b9f488-0b2c-45a9-85a7-020d9647e6b8.png">
</p>

### **Flag/Password**
```
IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```
  
---
  
## **Bandit Level 11 → Level 12**
### **Level Goal**

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

### **Commands you may need to solve this level** ###
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### **Solution**
- Use cat command
```
cat data.txt
```
- It displays weird strings. As per instructions, we can decode it using rot13 with the ranged arguments used for rotating 13 positions of a letter
```
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/149617649-7bd0cc9d-94bf-478d-bbea-094c588f9349.png">
</p>

### **Flag/Password**
```
5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```
  
---
  
## **Bandit Level 12 → Level 13**
### **Level Goal**

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

### **Commands you may need to solve this level** ###
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file

### **Solution**
- Create a directory under /tmp
```
mkdir /tmp/<dir_name>
```
- Copy the data.txt to a new directory created earlier
```
cp data.txt /tmp/<dir_name>
```
- Move to the directory
```
cd /tmp/<dir_name>
```
- Use cat command
```
cat data.txt
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186361141-20a7a74c-3205-43b2-8540-a1d11d5e24d3.png">
</p>

- Use xxd command to reverse this hex dump, and it will show some weird characters
```
xxd -r data.txt
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186363444-93423e01-f652-43b5-8fcd-34e3c193c584.png">
</p>

- Output the data to a new file using ">" command
```
xxd -r data.txt > data
```
- Now, check the file type
```
file data
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186364377-07c96774-3816-4188-aa23-e0ecdee2d040.png">
</p>

<p align="center">
  This is a gzip compressed file
</p>

- Rename the file to its corresponding extension name ".gz"
```
mv data data2.bin.gz
```
- Unzip the file named "data2.bin.gz"
```
gunzip data2.bin.gz
```
- Check the file type of file named "data"
```
file data2.bin
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186366523-303c1b9d-7c88-44ba-9b62-3d3c0e9cd957.png">
</p>

<p align="center">
  This is a bzip2 compressed file
</p>

- Rename the file to its corresponding extension name ".bz"
```
mv data2.bin data3.bin.bz
```
- Unzip the file named "<span>data3.bin.bz</span>"
```
bzip2 -d data3.bin.bz
```
- REPEAT THE PROCESS (check the file type → rename the file → unzip the file to its corresponding file type [gzip, bzip2, tar])

```
file data3.bin
mv data3.bin data4.bin.gz
gunzip data4.bin.gz

file data4.bin
mv data4.bin data5.bin.tar
tar xf data5.bin.tar

file data5.bin
mv data5.bin data6.bin.tar
tar xf data6.bin.tar

file data6.bin
mv data6.bin data7.bin.bz
bzip2 -d data7.bin.bz

file data7.bin
mv data7.bin data8.bin.tar
tar xf data8.bin.tar

file data8.bin
mv data8.bin data9.bin.gz
gunzip data9.bin.gz
```
- Check the file type
```
file data9.bin
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186368519-9e9d2d50-fcd3-46d5-8db7-c17fe58880ff.png">
</p>

<p align="center">
  This is an ASCII text file
</p>

- View the file
```
cat data9.bin
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186369238-6ef39c76-15a7-4e74-b3ab-1ddd5e54cd6b.png">
</p>

### **Flag/Password**
```
8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```
---
  
## **Bandit Level 13 → Level 14**
### **Level Goal**

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

### **Commands you may need to solve this level** ###
ssh, telnet, nc, openssl, s_client, nmap

### **Solution**

- Use the cat command and it will display RSA private key that is useful for next level
```
cat sshkey.private
```
- Disconnect from this level and go to system's home directory
- Perform the "scp" command to copy the "sshkey.private" file to our system's current directory
```
scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private /home/<user>/Documents
```
- Then use the "ssh" command to bandit 14 with the flag "-i" and pass the file that has the private key for bandit 14
```
ssh bandit14@bandit.labs.overthewire.org -p 2220 -i sshkey.private
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186372832-48775e93-ed9d-4fc4-893e-2d983867d6f2.png">
</p>

- But, it requires a password that we don't know
- Use "chmod" command to change the permissions of the file, use 400 to permit the owner for reading this file
```
chmod 400 ~/.ssh/sshkey.private
```
- Try connecting again 
```
ssh bandit14@bandit.labs.overthewire.org -p 2220 -i sshkey.private
```
- Now, we are connected to bandit 14
- To get the flag for this level, go to /etc/bandit_pass/bandit14
```
cd /etc/bandit_pass/bandit14
```

### **Flag/Password**
```
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```

---
  
## **Bandit Level 14 → Level 15**
### **Level Goal**

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

### **Commands you may need to solve this level** ###
ssh, telnet, nc, openssl, s_client, nmap

### **Solution**
- Connect to the localhost port 30000 using "nc" command
```
nc localhost 30000
```
- Now, it will prompt and it needs to enter the password for this level
```
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```
- It will display the flag automatically

### **Flag/Password**
```
BfMYroe26WYalil77FoDi9qh59eK5xNr
```
  
---
  
## **Bandit Level 15 → Level 16**
### **Level Goal**

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

### **Commands you may need to solve this level** ###
ssh, telnet, nc, openssl, s_client, nmap

### **Solution**
- Connect to the localhost port 30001 using "openssl" command
```
openssl s_client -connect localhost:30001
```
- Now, it will prompt and it needs to enter the password for this level
```
BfMYroe26WYalil77FoDi9qh59eK5xNr
```
- It will display the flag automatically

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186377472-c8b124bd-0059-46e6-af68-08896c4e55b1.png">
</p>

### **Flag/Password**
```
cluFn7wTiGryunymYOu4RcffSxQluehd
```
  
---
  
## **Bandit Level 16 → Level 17**
### **Level Goal**

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

### **Commands you may need to solve this level** ###
ssh, telnet, nc, openssl, s_client, nmap

### **Solution**
- Find open ports between 31000 to 32000 on localhost using "nmap" command
```
nmap localhost -p 31000-32000
```
- Now, nmap will tell us the open ports [31046, 31518, 31691, 31790, 31960] and connect to each ports to see the output
- But, port 31790 has a different output, use "openssl" command and connect to this port
```
openssl s_client -connect localhost:31790
```
- It will prompt you for the password, type the password of this level
```
cluFn7wTiGryunymYOu4RcffSxQluehd
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186381723-ecb4787f-c9b0-412d-bf52-6cc7f0560b90.png">
</p>

- Copy the whole RSA private key text
- Disconnect from this level and go to system's Documents directory
- Use "nano" command, paste the RSA private key and save as "rsa.private"
- Now, we need to permit the owner to read the file named "rsa.private" using chmod 
```
chmod 400 rsa.private
```
- Try to connect to the next level (Bandit 17)
```
ssh bandit17@bandit.labs.overthewire.org -p 2220 -i /home/<user>/Documents/rsa.private
```
- Once you're in, go to /etc/bandit_pass/bandit17 directory to check the password for this level and view the file
```
cat /etc/bandit_pass/bandit17
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186383839-8b608b3e-637d-4f29-a5a4-48ec94d79215.png">
</p>

### **Flag/Password**
```
xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn
```
  
---
  
## **Bandit Level 17 → Level 18**
### **Level Goal**

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

### **Commands you may need to solve this level** ###
cat, grep, ls, diff

### **Solution**
- We will be using "diff command" to view and differentiate the two files
```
diff --normal passwords.new passwords.old
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186388993-66dff626-ffd5-4800-adca-4abc2a5eeee9.png">
</p>

- The flag is on the first line

### **Flag/Password**
```
kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
```
  
---
  
## **Bandit Level 18 → Level 19**
### **Level Goal**

The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

### **Commands you may need to solve this level** ###
ssh, ls, cat

### **Solution**
- We can't connect to this level by normal logging in the credential using ssh
- Use the "ssh" command with the flag "-t" to allow us using the terminal and spawn a bash shell
```
ssh -t bandit18@bandit.labs.overthewire.org -p 2220 /bin/sh
```
- Check the current working directory
```
pwd
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186392674-c389facf-8fb8-4968-9286-9bc4afda9a60.png">
</p>

- Now, we are at home directory
- List the files in this directory 
```
ls
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186392957-44058c42-2a13-4372-b9ef-76cd35bdbcea.png">
</p>

- View the file named "readme"
```
cat readme
```

### **Flag/Password**
```
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```
  
---
  
## **Bandit Level 19 → Level 20**
### **Level Goal**

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

### **Commands you may need to solve this level** ###
none

### **Solution**
- View the file named "bandit20-do", it will show random characters and a "Run a command as another user" phrase
```
cat bandit20-do
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186394219-6ac93fe1-8272-4f33-8399-140e00446f5a.png">
</p>

- Now, I will try to run this file
```
./bandit20-do
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186394604-71fbd0ab-749f-4965-b3bd-a58f2db4e179.png">
</p>

- So, as mentioned above, I will try to run this executable file with id next to it
- Check the id for this bandit level
```
./bandit20-do id
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186395122-0a5627be-d16d-4b98-915c-6b82a235dac9.png">
</p>

- Run the executable file with id "euid=11020", and specify the command that we are using to view the flag on /etc/bandit_pass/bandit20
```
./bandit20-do euid=11020 cat /etc/bandit_pass/bandit20
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186396083-aa1b37d5-b766-4e6d-bdb0-b2c2f7964056.png">
</p>

### **Flag/Password**
```
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```
  
---
  
## **Bandit Level 20 → Level 21**
### **Level Goal**

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think
### **Commands you may need to solve this level** ###
ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)

### **Solution**
- Check the file type of file named "suconnect"
```
file suconnect 
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186440968-7affafac-add7-4c6c-b970-cb175b7e3a0a.png">
</p>

<p align="center">
  The file is executable
</p>

- Try to run the file
```
./suconnect
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186441295-188e5633-f64a-4d7a-ad7c-d1c229839f85.png">
</p>

- But, first we use netcat to create a connection on port 12345
```
nc -l -p 12345
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186442394-93545a58-3859-4aac-91b0-da3ef05f1e4f.png">
</p>

<p align="center">
  A blank prompt
</p>

- Now, paste the flag for this level

```
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```
- Open another instance of bandit 20 on a separate tab of terminal, then run the executable file with the port 12345 (same as the port we created earlier)

```
./suconnect 12345
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186443464-db3b7075-6384-4949-a4e7-df97edb4b92f.png">
</p>

<p align="center">
  Second instance
</p>

- It will transmit the flag to the other tab (main terminal)

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/186444417-91f74583-fef1-4933-a3c6-b1dfede4118d.png">
</p>

### **Flag/Password**
```
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```
  
---
  
</div>
