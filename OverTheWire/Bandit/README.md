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
  
  
  
  
  
  
  
  
  
  
  
</div>
