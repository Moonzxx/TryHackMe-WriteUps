# Sudo Agent



## Author

Munirah Binte Mohamad



## Tasks



### [Task 2 - Enumerate]

Enumerate the machine and get all the important information.



**Qn1. How many open ports?** 

```Kali
nmap -sC -sV -A -Pn <Target IP Address>
```

> -sV : Get the version of the services running on the ports.
>
> -A: Detect OS and Services
>
> -Pn: Scan port numbers (It was redundant, in this case)

<img src="D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Nmap.jpg" alt="Nmap"  />



**Answer: 3**



**Qn2. How you redirect yourself to a secret page? **



Since port 90 is open, it means we can access the HTTP of the IP Address. Thus, open up a browser and enter the ip address of the target machine.



![Webpage](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Webpage.jpg)



**Answer: User-Agent**



**Qn3. What is the agent name?**

We know that Agent R exist. So, let's try finding Agent's R homepage.

> -A : Identify User-Agent string
>
> -L / -v : Verbose information (Long vers. information)

![Curl](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Curl.jpg)


Alright, at least we managed to get Agent R's page. Since the agent's names are in letters, we should try all 26 alphabets until we find something.

I tried A and B but it produces the same body context as R. But, C produced a different result.



<img src="D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Curl C.jpg" alt="Curl C" style="zoom:150%;" />

Answer: Chris





### [Task 3] Hash cracking and brute-force

Done Enumerating the machine? Time to brute your way out.



<u>**Qn1. FTP password**</u>

Using Hydra to brute force the FTP login.

```
hydra -l chris -P /usr/share/wordlists/rockyou.txt -vV <Target IP Addr> ftp
```

![Hydra ftp](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Hydra ftp.jpg)



Use the command below to access the FTP Server.

```
ftp <Target IP Addr>
```



![ftp dir](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\ftp dir.jpg)



After gaining access to the FTP Server, use the following command to download the file to your local computer current directory.

```Kali
mget <file name>
```



![Repeat same rest](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Repeat same rest.jpg)



Repeat the same steps for the other 2  files to download them to your local directory.

Once the files have been download, read the "To_agentJ.txt".



![agent j](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\agent j.jpg)



<u>**Qn2. Zip File Password**</u>

Form the textfile above, we know that the password is stored in either one of the pictures. Use the binwalk command to check if there is anything in the pictures.

![binwalk](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\binwalk.jpg)



It seems like cutie.png has a zip data compressed in the file. Thus, to extract the files within the PNG file, we can sue the binwalk command.



![binwalk extract](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\binwalk extract.jpg)



When I tried to unzip the file using the unzip command, it failed because the zip file was encrypted. Therefore, I decided to use zip2john to read the hash and use the john command to crack the hash.



![retriving passwd](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\retriving passwd.jpg)

 Once the password has been revealed, use the following command to extract the secret text file in the picture.



![unzip zip file with passwd](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\unzip zip file with passwd.jpg)



Read the secret file.



![secret txt file](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\secret txt file.jpg)



It seems like the word is encrypted, I decided to decode it using base64 and it works!



![passwd decoded](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\passwd decoded.jpg)



To check for information on the secret file in the picture, use the command below.:



![Steghide info](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Steghide info.jpg)



Since it has been confirmed that there secret file is inside, use the command below to extract the secret file from the JPG file.

![Steghide extraction](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Steghide extraction.jpg)



![Message steg](D:\Digital Forensics\CTF\TryHackMe\Sudo Agent\Message steg.jpg)





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