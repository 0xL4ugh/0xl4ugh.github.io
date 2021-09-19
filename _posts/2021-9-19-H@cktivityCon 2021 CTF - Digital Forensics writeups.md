---
layout: post
title:  H@cktivityCon 2021 CTF - Digital Forensics Writeups                              # Title of the page
hide_title: false                                  # Hide the title when displaying the post, but shown in lists of posts
feature-img: "assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_1.png"              # Add a feature-image to the post
thumbnail: "assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_1.png"  # Add a thumbnail image on blog view
color: dufault                            # Add the specified color as feature image, and change link colors in post
bootstrap: true                                   # Add bootstrap to the page
author: xElessaway
excerpt_separator: <!--more-->
tags: [ctf, writeup, Forensics]
---
<h1>H@cktivityCon 2021 CTF - Digital Forensics Writeups    </h1>  
 <!--more-->

Hello, It's Ahmed Mahmoud(xElessaway), and this is my writeups for some challenges I've solved in H@cktivityCon CTF 2021.

```java
| CHALLENGE           | CATEGORY          | DIFFCULTY |
|---------------------|-------------------|-----------|
| Excellent           | Digital Forensics | Medium    |
| Bacon in a Haystack | Digital Forensics | Medium    |
| UHAHA               | Misc              | Medium    |
```



- Challenge Name 

  > Excellent

- Category 

  > Digital Forensics

- Description 

  > My computer crashed and I lost everything I was doing for work...

- Tools 

  >  it will only need a one tool from this list 

```java
1- Volatility
2- Linux Commands
3- LibreOffice
```

- Steps

In the challenge I provided a .bin file. So I tried to open it on Autopsy and FTK Imager but not working so I started to use Volatility on it.

First, I started to check the image info by using 

```java
python3 vol.py -f image.bin windows.info
	-f to select the image
```

Note: I used Volatility3 not Volatility2
if you will use Volatility2 you can use this command to get the profile of the image.

```java
python vol.py -f image.bin imageinfo
```

![Excellent_1](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_1.png)

So It's working on volatility now it's time to go psscan to check the process.

> Volatility3

```java
python3 vol.py -f image.bin windows.info
```

> Volatility2

```java
python vol.py -f image.bin --profile=the_profile_you_got psscan
```

![Excellent_2](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_2.png)

Okay I got so many process in the scan so I went through process to check if there is any suspicious process or something can crash the pc. But I didn't see something interesting except **LibreOffice** So I went to check the cmd if he used it.

> Volatility3

```java
python3 vol.py -f image.bin windows.cmd
```

> Volatility2

```java
python vol.py -f image.bin --profile=the_profile_you_got cmdscan
```



![Excellent_3](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_3.png)

Okayy this is interesting I've found ("C:\Users\congon4tor\Desktop\flag.ods") so Time to do file scan and get this file.

> Volatility3

```java
python3 vol.py -f image.bin windows.filescan | grep flag.ods
```

> Volatility2

```java
python vol.py -f image.bin --profile=the_profile_you_got filescan | grep flag.ods
```



![Excellent_4](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_4.png)

and I got the offset of the file. So let's dump it and open it on LibreOffice.

> Volatility3

```java
python3 vol.py -f image.bin windows.dumpfiles --virtaddr 0xaa873a6567c0
	--virtaddr To select the specific offset of the file.
```

> Volatility2

```java
python vol.py -f image.bin --profile=the_profile_you_got dumpfiles -Q 0xaa873a6567c0 -D output
	-Q To select the specific offset of the file.
	-D to choose the folder that I want to dump to.
```

So After Dumping the file and open it on LibreOffice I got the flag.

![Excellent_Flag](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_Flag.png)

> **Flag is : flag{4b02ee4e7b62139152e8d0d4373a7c3d}**





```java
| CHALLENGE           | CATEGORY          | DIFFCULTY |
|---------------------|-------------------|-----------|
| Excellent✔️        | Digital Forensics | Medium    |
| Bacon in a Haystack | Digital Forensics | Medium    |
| UHAHA               | Misc              | Medium    |
```



- Challenge Name 

  > Bacon in a Haystack

- Category 

  > Digital Forensics

- Description 

  > I dropped my bacon in a haystack. :-/
  > Any ideas how we can find it?

- Tools 

  >  it will only need a one tool from this list 

```java
1- Linux Commands
```

- Steps

In the challenge I provided a .zip file that contains many many logs.![Bacon_1](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_1.png)

I started to go through files and I notice that there are http and ssl logs.![Bacon_3](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_3.png)

So I split logs and put these logs into folder. So it's more easy to search on it

![Bacon_2](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_2.png)

I googled on how to grep all sites on fiiles and I got this command 

```java
grep -Po '([a-z]+\.)+[a-z]+(/\w+)*' file_name
so I greped on all the logs using this
grep -Po '([a-z]+\.)+[a-z]+(/\w+)*' *
```

I notice that there are Github so I tried to grep it and uniq it to be more clear to see

```java
grep -Po '([a-z]+\.)+[a-z]+(/\w+)*' * | sort | grep github | uniq
```

![Bacon_4](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_4.png)

and yes I got a github page [Sketchysite](https://sketchysite.github.io/) I opened it and I got the flag :D

![Bacon_Flag](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_Flag.png)

> **Flag is : flag{8626fe7dcd8d412a80d0b3f0e36afd4a}**

```java
| CHALLENGE             | CATEGORY          | DIFFCULTY |
|-----------------------|-------------------|-----------|
| Excellent✔️           | Digital Forensics | Medium    |
| Bacon in a Haystack✔️ | Digital Forensics | Medium    |
| UHAHA                  | Misc              | Medium    |
```



- Challenge Name 

  > UHAHA

- Category 

  > Misc

- Description 

  > I dropped my bacon in a haystack. :-/
  > Any ideas how we can find it?

- Tools 

  >  it will only need a one tool from this list 

```java
1- Google
2- Scripting
3- LibreOffice
```

- Steps

In the challenge I provided a non extension file. So I used file command on it to check the file type.

![uhaha_1](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/uhaha_1.png)

I got UHarc Archive data so I don't know what is this so it's time to visit my best friend Google to ask him about this type of data. and as usual I got the answer.

![uhaha_2](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/uhaha_2.png)



I know now that UHARC files has extension (  **.UHA** ) so I put the extension. but I don't know how to open this type of files I tried 7z and winrar but nothing so I went again to my best friend Google to ask him about how to extract file from UHARC files. and I got this tool (**UHARC**)

so let's check the syntax we need to extract the file with this tool.

![Uhaha_3](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Uhaha_3.png)

so the syntax must be like this:

```java
./UHARC.EXE e -pw[PasswordHere] FileName
```

after this I tried to it works but I don't have the password so back to the description he told me that I just need the top hundred passwords in `rockyou.txt`wordlist so I won't try passwords manually of course. So it's time to write small script to try all passwords.

```python
import os
import sys
passwords = ["123456","12345","123456789","password","iloveyou","princess","1234567","rockyou",...] #I don't know why I put passwords in list not just read them from file xDD

for b in  range(1,100,1):
	for i in passwords:
		os.system("C:/Users/ahmed/Desktop/Twitch/z/UHARC.EXE e -pw"+i+" uhaha.uha")
```

after trying this it works. but I got another file so I have to put the extension again.

what we need to do

 					Put Extension .uha > run the command to test all passwords > if we extract > remove old file > rename the extracted file with the extnsion

so let's do this.

```python
import os
import sys

passwords = ["123456","12345","123456789","password","iloveyou","princess","1234567","rockyou",...] #I don't know why I put passwords in list not just read them from file xDD

for b in  range(1,100,1):
	for i in passwords:
		os.system("C:/Users/ahmed/Desktop/Twitch/z/UHARC.EXE e -pw"+i+" uhaha.uha")

	os.remove("uhaha.uha")
	os.rename("uhaha" ,"uhaha.uha")
```

![Uhaha_4](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Uhaha_4.png)

and yes finally we got the flag.

![Uhaha_Flag](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Uhaha_Flag.png)

> **Flag is : flag{ec8753d9932766b1724618b5ad12de13}**

```java
| CHALLENGE              | CATEGORY          | DIFFCULTY |
|------------------------|-------------------|-----------|
| Excellent✔️           | Digital Forensics | Medium    |
| Bacon in a Haystack✔️ | Digital Forensics | Medium    |
| UHAHA✔️               | Misc              | Medium    |
```

and special thanks for mmox <3
