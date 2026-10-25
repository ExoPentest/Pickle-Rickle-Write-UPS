# Pickle-Rickle-Write-UPS
This is the solution for tryhackme's pickle rickle easy lab. This room mainly focuses on theoretical linux knowledge rather than heavily using exploits.
The key here is linux basics & enumeration
# Enumeration
We should always PING the IP to check for availability.
We can use many tools here gang for enumeration but we will use classic nmap :- 

# NMAP 
```nmap -sS -sV <TARGET_IP>```

<img width="1638" height="342" alt="Screenshot_২০২৬১০২৬_০৩৫০৪৬" src="https://github.com/user-attachments/assets/3240581e-969b-4346-b1c3-a710701a94d5" />

- **Perhaps**
- sS - TCP SYN SCAN
- sV - Version SCAN
- These are the most common nmap flags that penetration testers use to check for open ports and service version.

**THIS GAVE US 2 OPEN PORTS 1 HTTP 2ND SSH**
- HTTP - HYPERTEXT TRANSFER PROTOCOL
- SSH - SECURE SHELL BETTER THAN TELNET

# HTTP MAIN FOCUS ;-
here our main focus will be HTTP we will went through some rabbit holes but the methodology will be same
we may use many tools like gobuster,dirb,ffuf. For this we will be using gobuster

# GOBUSTER
```gobuster dir -u <TARGET_IP_URL> -w <PATH_TO_WORDLISTS> -x <EXTENSION>```


<img width="1424" height="644" alt="Screenshot_২০২৬১০২৬_০৪১৯৪৩" src="https://github.com/user-attachments/assets/60bb9d46-846d-45d6-b52c-97e46246d6c9" />

- **Perhaps**
- dir - directory enumeration
- -u - target url
- -w - path mainly seclists or wordlists
- -x - extensions like .php,.txt,.html,.xml,.yml

# PAGE SOURCE CODE
In CTFs Page source code mostly carries some info but not everytime.


<img width="3480" height="1542" alt="Screenshot_২০২৬১০২৬_০২৫৭১৫" src="https://github.com/user-attachments/assets/782db30a-f32b-428b-bf81-be41d9ba87e9" />
This is mentioned as a username we will note that.

# Directory Enumeration Resutls
The Results gave us things like robots.txt and login.php

<img width="1278" height="578" alt="Screenshot_২০২৬১০২৬_০২৫২১৯" src="https://github.com/user-attachments/assets/ebc5c22f-2399-4679-af27-fd2ba2220192" />

**Could potentially be a password lets try both credentials**
```REDACTED:REDACTED```

<img width="1905" height="978" alt="Screenshot_২০২৬১০২৬_০৩০১০৫" src="https://github.com/user-attachments/assets/d76bcf2e-fcf4-44be-8b4c-24be444a6864" />

Lucky us it worked

**FLAGS**
This is where linux commands comes handy than normal exploits.

<img width="3810" height="1956" alt="Screenshot_২০২৬১০২৬_০৩০২২৭" src="https://github.com/user-attachments/assets/31776663-554a-453a-bfbe-c5fa1b5d4017" />

The website dosen't allow cat but allows strings,less,ls,more,etc.
Its the things that will help us out throughout the lab.

<img width="1824" height="777" alt="Screenshot_২০২৬১০২৬_০৩৫৩৩৭" src="https://github.com/user-attachments/assets/7911e27a-5b33-41c4-9269-f23e7bfd1b95" />

Lets find out the rick guy here

<img width="1824" height="777" alt="Screenshot_২০২৬১০২৬_০৩৫৭০১" src="https://github.com/user-attachments/assets/561318c3-042a-4f21-8c69-c8a218e78116" />

Funny we got him this was valid cause /home has the users 

<img width="3648" height="1554" alt="Screenshot_২০২৬১০২৬_০৩৫৮১৬" src="https://github.com/user-attachments/assets/56f22d51-a733-46b0-b7ed-567223a7b097" />

**NOTICE**
In Linux when making a directory or a file that has a space it has to be enclosed in quotations this cannot be avoided.
You can try this by making one,

**ROOT**
We can see
```sudo -l```
This gives us really really good info
Sudo -l usually stands for listing the user permission in running sudo

<img width="2574" height="1412" alt="Screenshot_২০২৬১০২৬_০৪০৩০৬-2" src="https://github.com/user-attachments/assets/fb03317d-b4da-4196-8cbf-8f459555090b" />

Thats it anyone can run sudo as this lab dosen't allow reverse shell or Sudo su to directly get root we  will do

Sudo su means change to root lets just know if its out of scope here

<img width="1287" height="706" alt="Screenshot_২০২৬১০২৬_০৪০৪৩৮" src="https://github.com/user-attachments/assets/054630b0-32b3-4cf8-acd7-bdd09ed650ff" />

now we just use strings to view the content 

<img width="2574" height="1412" alt="Screenshot_২০২৬১০২৬_০৪০৫৩০" src="https://github.com/user-attachments/assets/453dd849-ddb2-42ee-b4a0-1f9ea87fc835" />

***Amazing we got the three ingredients and hopefully saved from pickle***
**I hope you enjoyed the write-up it is probably the first challenge for many was also for mine it covers many stuff that will you know be handy on almost any challenges**


***THANK YOU***
# HAPPY HACKING ALWAYS LEGAL 
# SYNONYM REVERSES














