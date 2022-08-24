<div align="justify">
  
# **Inclusion**

## **A beginner level LFI Challenge**

### What is Local File Inclusion (LFI)?
Basically, A Local File Inclusion
> Allows an attacker to read (and sometimes execute) files on the victim machine. This can be very dangerous because if the web server is misconfigured and running with high privileges, the attacker may gain access to sensitive information. If the attacker is able to place code on the web server through other means, then they may be able to execute arbitrary commands.
<p align="center"> 
<a href="https://www.offensive-security.com/metasploit-unleashed/file-inclusion-vulnerabilities/">
offensive-security.com
</a>
</p>

### **Solution**

Deploy the machine.
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/154020246-97d2f0d3-e36d-49cc-80a4-e91b7dac7e7b.png"
</p>
  
We can see that this is a normal blog webpage. At first, I explore the website and look for parameters. If we click the "View details" buttons, we can now have the parameter "name=".
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/154020698-fc3cec40-b9f1-4ffa-a623-85361db042ad.png"
</p>
  
Now, Insert our LFI payload to "name=" parameter to gain sensitive information on the website. I use burpsuite to capture the request and edit the parameter value, use the basic payload "../../../../../../../etc/passwd" to access the passwd file.
```
http://10.10.66.111/article?name=../../../../../../../etc/passwd
```
and it shows some accounts that caught my attention.
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/154022207-484a234c-d15a-473d-af62-453092358c8c.png"
</p>
  
We will focus on the falconfeast and root account because I assume that the flag is stored in their directory.
So, I came up with the idea that the user.txt is stored in /home/falconfeast
 
```
http://10.10.66.111/article?name=../../../../../../../home/falconfeast/user.txt
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/154022694-57ec60e8-c9b0-434f-8a97-208be7352511.png"
</p>
  
It shows random numbers, and it is the user flag!!!

Now, for the root flag, I assume that the file is in /root
  
```
http://10.10.66.111/article?name=../../../../../../../root/root.txt
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/93600181/154022707-70872241-6083-497f-aafa-d4f00ee07b1c.png"
</p>
  
Again, it shows random numbers and it is the root flag!!!
  
### **Flag**

user flag
```
60989655118397345799
```
root flag
```
42964104845495153909
```
  
---
  
</div>
