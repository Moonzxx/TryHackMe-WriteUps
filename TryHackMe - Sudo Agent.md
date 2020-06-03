# Sudo Agent



## Author

Munirah Binte Mohamad



## Tasks



### [Task 2 - Enumerate]

Enumerate the machine and get all the important information.

```Kali
nmap -sC -sV -A -Pn <Target IP Address>
```

> -sV : Get the version of the services running on the ports.
>
> -A: Detect OS and Services
>
> -Pn: Scan port numbers (It was redundant, in this case)

<img src="D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Nmap.jpg" alt="Nmap"  />



Qn1, How many open ports? 3

Since port 90 is open, it means we can access the HTTP of the IP Address. Thus, open up a browser and enter the ip address of the target machine.



![Webpage](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Webpage.jpg)



Qn2. How you redirect yourself to a secret page? User-agent

We know that Agent R exist. So, let's try finding Agent's R homepage.

> -A : Identify User-Agent string
>
> -L / -v : Verbose information (Long vers. information)

![Curl](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Curl.jpg)


Alright, at least we managed to get Agent R's page. Since the agent's names are in letters, we should try all 26 alphabets until we find something.

I tried A and B but it produces the same body context as R. But, it was different when I found C.



<img src="D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Curl C.jpg" alt="Curl C" style="zoom:150%;" />

Qn3. What is the agent name? Chris





### [Task 3] Hash cracking and brute-force

Done Enumerating the machine? Time to brute your way out.

```
hydra -l chris -P /usr/share/wordlists/rockyou.txt -vV 10.10.243.6 ftp
```

![Hydra ftp](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Hydra ftp.jpg)



Qn1. FTP password

![ftp dir](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\ftp dir.jpg)



![Repeat same rest](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Repeat same rest.jpg)

Repea the same for all thee

![agent j](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\agent j.jpg)

Qn2. Zip File Password

![binwalk](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\binwalk.jpg)



![binwalk extract](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\binwalk extract.jpg)



![retriving passwd](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\retriving passwd.jpg)

![unzip zip file with passwd](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\unzip zip file with passwd.jpg)



![secret txt file](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\secret txt file.jpg)



![passwd decoded](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\passwd decoded.jpg)



![Steghide info](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Steghide info.jpg)





![Steghide extraction](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Steghide extraction.jpg)



![Message steg](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Message steg.jpg)



Qn3. Steg Password

Qn4.Who is the other agent (in full name)?

Qn5. SSH password



### [Task 4 - Capture the User flag]

QN1. What is the user flag?

![SSH JAMES](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\SSH JAMES.jpg)



// ForgTask 5ot to tae the picture  of user cat

cat user-flag.txt



![scp image](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\scp image.jpg)



![Google reverse](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Google reverse.jpg)



![incident](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\incident.jpg)



Qn2. What is the incident of the phot called?



### [Task 5] Privilege Escalation



![whoami](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\whoami.jpg)



![sudo version](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\sudo version.jpg)



![james sudo](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\james sudo.jpg)



![cve](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\cve.jpg)



![her](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\her.jpg)



![Information on CVE](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Information on CVE.jpg)



![final](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\final.jpg)