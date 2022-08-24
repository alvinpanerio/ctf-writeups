<div align="justify">
  
# **Pickle Rick**

#### This Rick and Morty themed challenge requires you to exploit a webserver to find 3 ingredients that will help Rick make his potion to transform himself back into a human from a pickle.

### **Solution**

Deploy the machine, and get connected to OpenVPN.
First, Let's do reconnaissance and scanning on the given URL/IP address using NMAP
  
```
sudo nmap -sS -sV <IP_ADDRESS>
```
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158535573-c695613b-c114-482f-9b4f-8963430c673e.png">
</p>
  
The given IP address has open ports, 22 (ssh) and 80 (http).
So, let's take a look in the browser on how the website works.

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158536073-97bb0471-5ec1-4357-8d1b-911e3908684e.png">
</p>

<p align="center">
  A static webpage
</p>
  
Now, right click the webpage to view the page source.
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158536430-ebf22883-4662-4637-aaac-98df5ec0c253.png">
</p>
  
On the line 28-34 (the photo was cut), there is a comment that says, R1ckRul3s is the username (Take note of this part).
Now, we don't have any resources to explore. Next step will be, directory/file bruteforcing using GoBuster on the given IP address.
Before I proceed, I modified 'common.txt' wordlist from dirb because it has no *.php words. This is the wordlist --> <a href="https://github.com/alvinpanerio/CTF-writeups/blob/main/TryHackMe/Pickle-Rick/wordlist.txt">wordlist.txt</a>

Now, run GoBuster
  
```
gobuster dir -e -t 10 -u <IP_ADDRESS/WEBSITE_URL> -w wordlist.txt
```
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158537549-906e5ccf-d871-4af8-af52-fc4e29f28030.png">
</p>

<p align="center">
  Gobuster result
</p>
  
We can see that there are 2 new files that has status code of 200 and 1 directory for status 301. Now, visit the /assets directory.

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158537895-573ae483-8b2b-4da8-950a-834b9d6495ef.png">
</p>

<p align="center">
  /assets
</p>
  
Nothing interesting here, visit /robots.txt file
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158537965-504cfd2d-9431-4ceb-94fd-a22b89c28c5e.png">
</p>

<p align="center">
  /robots.txt
</p>
  
We found some sort of string that is important later (Take note of this part), let's move to the last one, /login.php file

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158538264-6b772211-57e0-4b70-8cf2-5e03f9f91f41.png">
</p>

<p align="center">
  /login.php
</p>
  
Now, we reach a portal login page.
  
Try to login using the credentials we saw earlier. 

```
Username: R1ckRul3s
Password: Wubbalubbadubdub
```
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158540595-8da400e5-9f8d-4502-83a9-2ae6d2e00f50.png">
</p>

<p align="center">
  /portal.php
</p>
  
We're logged in to the portal account and we can see that we can perform some commands on the field. Try some commands like whoami, pwd and ls.

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158541102-9d96c971-909c-449d-83f5-cc15236716bf.png" align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158541112-64988496-30a1-4d47-ae51-33097f2d3c4d.png" align="center">
</p>
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158541121-2f3f4ff8-b589-4120-b456-1cb03e8194e9.png">
</p>
  
There are some files in this directory and one of them is the interesting file here, the 'Sup3rS3cretPickl3Ingred.txt'
  
Try to look at it using 'cat' command
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158542011-9b649174-3a5b-485f-8e86-89e87e86fa69.png">
</p>
  
But, this is what happen when I try 'cat' command to all files. I assume that 'cat' command is not working here. I found some interesting logic here in the portal.php (I view it in the view page source)
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158542526-55dbf402-9c1a-4c6a-b9e0-c8181114a0cc.png">
</p>
  
We can't use 'cat, head, nano' commands etc. on the field because it performs the if/else statement logic here. At, the bottom there is a string encoded on base64. I will try to decode it.

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158542900-11fda8e5-232a-41b0-8a2f-9d2f02ffaa50.png">
</p>
  
I try to decode it many times using base64 to get the "rabbit hole" word, it does not make sense.

So, get back to previous issue, I try the alternative command, which is 'strings' command to get the value of 'Sup3rS3cretPickl3Ingred.txt'.

```
strings Sup3rS3cretPickl3Ingred.txt
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158543340-f44c93da-8e96-463a-bd2c-849b9eb10570.png">
</p>
  
It works! this is the first flag.
We will use 'strings' command to the other files.
For the clue.txt
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158543610-9780fba7-4718-4840-82e4-b11994039445.png">
</p>
  
It says that the other flag is accessible to other directory.
  
Next step, we will look into second flag. Most of the CTFs has the flags inside the user and root directory. But first, we will look into the user directory.
On the input field,

```
ls /
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158543904-5c364c0e-a8c4-4e27-b654-bfa26ba515dc.png">
</p>
  
There is a user and root directory! Let's explore.
 
```
ls /home/rick
```
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158544092-822ee369-0e6c-4ba3-b5e1-3e8cbce9b46f.png">
</p>
  
We can see that this is the second file that contains flag.

```
strings /home/rick/second\ ingredients
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158544250-cc77fd63-53d1-4cf2-8fb5-a2c23db8f3ae.png">
</p>
  
This is the second flag!
  
Now, for the final flag, I assume that this flag is on the root directory and we need permissions. So I check it with the command
sudo -l

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158544557-810ed831-1c2b-407c-9096-9b31a45d320a.png">
</p>

It does not require password/permissions when using sudo command. So go to /root directory,
 
```
sudo ls /root
```
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158544720-d8b26cbc-aad3-4232-9d3a-104aabf0ed3b.png">
</p>
  
We can see that this is the third file for the final flag!

```
sudo strings /root/3rd.txt
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/158544855-eca29cd0-a9c4-44a5-a20f-d65c9be84c88.png">
</p>

Yey! we completed the task. That's all for Pickle Rick Room.
 
### **Flag**

What is the first ingredient Rick needs?
```
mr. meeseek hair
```
Whats the second ingredient Rick needs?
```
1 jerry tear
```
Whats the final ingredient Rick needs?
```
fleeb juice
```
---
  
</div>

