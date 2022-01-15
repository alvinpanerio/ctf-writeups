# **GENERAL SKILLS**

## **1. Obedient Cat**
### **Description**

This file has a flag in plain sight (aka "in-the-clear"). Download flag.

### **Solution**
- Download the file
```
wget https://mercury.picoctf.net/static/0e428b2db9788d31189329bed089ce98/flag
```
- View the content of the 'flag' file
```
cat flag
```
### **Flag**
```
picoCTF{s4n1ty_v3r1f13d_2fd6ed29}
```

## **2. Python Wrangling**
### **Description**

Python scripts are invoked kind of like programs in the Terminal... Can you run this Python script using this password to get the flag?

### **Solution**
- Use wget command to get all files that are highlighted
- Type the command to decode the flag
```
Python3 ende.py -d flag.txt.en
```
### **Flag**
```
picoCTF{s4n1ty_v3r1f13d_2fd6ed29}
```

## **3. Wave a flag**
### **Description**

Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...

### **Solution**
- Download the file
```
wget https://mercury.picoctf.net/static/f95b1ee9f29d631d99073e34703a2826/warm
```
- Use this chmod +x command to make the file executable  
```
chmod +x warm
```
- Execute the file
```
./warm -h
```
### **Flag**
```
picoCTF{b1scu1ts_4nd_gr4vy_f0668f62}
```

