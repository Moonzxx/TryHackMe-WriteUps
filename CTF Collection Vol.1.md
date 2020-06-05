# CTF Collection Vol.1



## Description

Just another random CTF room created by me. Well, the main objective of the room is to test your CTF skills. For your information, vol. 1 consists of 20 tasks and all the challenges are extremely easy. Stay calm and Capture the flag :)



## Author

Munirah Binte Mohamd

### [ Task 2 ] What does the base said?

The flag is base64 encoded. Thus, to decrypt it, use the following command:

```
echo "<flag>" | base64 -d
```

<img src="D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\1.jpg" alt="1" style="zoom:150%;" />



### [ Task 3 ] Meta meta

Download the image.

To get more information about the image, use the following command:

```
exiftool <image>
```

![2](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\2.jpg)



### [Task 4 ] Mon, are we going to be okay?

DownTasload the image.

We know that something is hidden inside the image.

```
steghide info <image>
```

```
steghide extract -sf <image>
```

![3](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\3.jpg)

![3.1](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\3.1.jpg)



### [ Task 5 ] Erm....Magick

The hint mentions to highlight the text.

When I highlighted the text, I found the flag.

![4](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\4.jpg) 



### [ Task 6 ] QRrrrr

Download the image of the QR reader.

I used the website, https://online-barcode-reader.inliteresearch.com, to get the flag.

![5](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\5.jpg)



### [ Task 7 ] Reverse it or read it?

From the hint, I am guessing I have to reverse engineer the file.

![6](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\6.jpg)



### [ Task 8 ] Another decoding stuff

The hint given mentioned "base58". Thus, I used an online base58 decoder.

![7](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\7.jpg)



### [ Task 9 ] Left or Right

I used an online ROT decoder. 

From the website, when I decoded the flag using ROT1, the starting letter starts with 'P'. I know that the flag always starts with 'THM', so I counted the number of times it has to change to reach from 'P' to 'T'. That is how I discovered that the flag can be obtained by using ROT7.



![8](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\8.jpg)



### [ Task 10 ] Make a comment

The hint mentioned to "Check the html".

I was using Firefox's Web Developer to check the html.

![9](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\9.jpg)



### [ Task 11 ] Can you fix it?]

### [ Task 12 ] Read it

The hint mentioned "Reddit". 

![image-20200605172457703](C:\Users\munir\AppData\Roaming\Typora\typora-user-images\image-20200605172457703.png)



### [ Task 13 ] Spin my head

The hint mentioned "binaryfuck". 

![12](D:\Digital Forensics\CTF\TryHackMe\CTF Collection 1\12.jpg)





### [ Task 14 ] An exclusive!





### [ Task  15 ] Binary Walk

I used the binwalk command, and found that there is an "hello_there.txt". Once the file has been exfiltrated, look for the extracted directory and read the file.

![image-20200605173826949](C:\Users\munir\AppData\Roaming\Typora\typora-user-images\image-20200605173826949.png)



### [ Task 16 ] Darkness

The hint mentioned "Try Stegsolve".

Use the following command to run the jar file:

```
java -jar stegsolve.jar
```

![image-20200605195506543](C:\Users\munir\AppData\Roaming\Typora\typora-user-images\image-20200605195506543.png)



** Refer to https://www.youtube.com/watch?v=9-YczGtaIiY to understand better on how to use Stegsolve.



### [ Task 17 ] A sounding QR

Download the QR image.

Upload the image into a QR Decoder to be read.

![image-20200605200638545](C:\Users\munir\AppData\Roaming\Typora\typora-user-images\image-20200605200638545.png)



Listen to the soundcloud for the flag.



### [ Task 18 ] Dig up the past

The hint mentioned "Wayback Machine".

Thus, I searched on Google looking for "Wayback Machine". Look for the archive according to the information given by the question.



![image-20200605200919945](C:\Users\munir\AppData\Roaming\Typora\typora-user-images\image-20200605200919945.png)



### [ Task 19 ] Uncrackable

I decided to use CyberChef for this code as it allows various kinds of hash to be analysed.

We know that the format of the key starts with "TRYHACKME". So, I used "TRYHACKME" as the key and got the following output.

![image-20200605201628307](C:\Users\munir\AppData\Roaming\Typora\typora-user-images\image-20200605201628307.png)

Im going to use that output as the key so that they key output now will start with "TRYHACKME".

![image-20200605201826526](C:\Users\munir\AppData\Roaming\Typora\typora-user-images\image-20200605201826526.png)



### [  Task 20 ] Small bases

There are base2, base10, and base 16. So, I decided to experiment with the bases and have them converted into ASCII.

To get the flag, it has to be converted from Decimal -> Hex and Hex -> ASCII.



![image-20200605202714544](C:\Users\munir\AppData\Roaming\Typora\typora-user-images\image-20200605202714544.png)

 

### [  Task 21 ] Read the packet

This packet can be analysed usign Wireshark.

I decided to look into the HTTP protocol.



![image-20200605204947457](C:\Users\munir\AppData\Roaming\Typora\typora-user-images\image-20200605204947457.png)