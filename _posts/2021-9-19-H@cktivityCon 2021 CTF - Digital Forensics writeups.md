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

```css
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

```
1- Volatility
2- Linux Commands
3- LibreOffice
```

- Steps

In the challenge I provided a .bin file. So I tried to open it on Autopsy and FTK Imager but not working so I started to use Volatility on it.

First, I started to check the image info by using 

```
python3 vol.py -f image.bin windows.info
	-f to select the image
```

Note: I used Volatility3 not Volatility2
if you will use Volatility2 you can use this command to get the profile of the image.

```
python vol.py -f image.bin imageinfo
```

![Excellent_1](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_1.png)

So It's working on volatility now it's time to go psscan to check the process.

> Volatility3

```
python3 vol.py -f image.bin windows.info
```

> Volatility2

```
python vol.py -f image.bin --profile=the_profile_you_got psscan
```

![Excellent_2](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_2.png)

Okay I got so many process in the scan so I went through process to check if there is any suspicious process or something can crash the pc. But I didn't see something interesting except **LibreOffice** So I went to check the cmd if he used it.

> Volatility3

```
python3 vol.py -f image.bin windows.cmd
```

> Volatility2

```
python vol.py -f image.bin --profile=the_profile_you_got cmdscan
```



![Excellent_3](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_3.png)

Okayy this is interesting I've found ("C:\Users\congon4tor\Desktop\flag.ods") so Time to do file scan and get this file.

> Volatility3

```
python3 vol.py -f image.bin windows.filescan | grep flag.ods
```

> Volatility2

```
python vol.py -f image.bin --profile=the_profile_you_got filescan | grep flag.ods
```



![Excellent_4](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_4.png)

and I got the offset of the file. So let's dump it and open it on LibreOffice.

> Volatility3

```
python3 vol.py -f image.bin windows.dumpfiles --virtaddr 0xaa873a6567c0
	--virtaddr To select the specific offset of the file.
```

> Volatility2

```
python vol.py -f image.bin --profile=the_profile_you_got dumpfiles -Q 0xaa873a6567c0 -D output
	-Q To select the specific offset of the file.
	-D to choose the folder that I want to dump to.
```

So After Dumping the file and open it on LibreOffice I got the flag.

![Excellent_Flag](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Excellent_Flag.png)

> Flag is : flag{4b02ee4e7b62139152e8d0d4373a7c3d}





```markdown
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

```
1- Linux Commands
```

- Steps

In the challenge I provided a .zip file that contains many many logs.![Bacon_1](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_1.png)

I started to go through files and I notice that there are http and ssl logs.![Bacon_3](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_3.png)

So I split logs and put these logs into folder. So it's more easy to search on it

![Bacon_2](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_2.png)

I googled on how to grep all sites on fiiles and I got this command 

```
grep -Po '([a-z]+\.)+[a-z]+(/\w+)*' file_name
so I greped on all the logs using this
grep -Po '([a-z]+\.)+[a-z]+(/\w+)*' *
```

I notice that there are Github so I tried to grep it and uniq it to be more clear to see

```
grep -Po '([a-z]+\.)+[a-z]+(/\w+)*' * | sort | grep github | uniq
```

![Bacon_4](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_4.png)

and yes I got a github page [Sketchysite](https://sketchysite.github.io/) I opened it and I got the flag :D

![Bacon_Flag](https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/hacktivitycon-Forensics-xElessaway/Bacon_Flag.png)

> Flag is : flag{8626fe7dcd8d412a80d0b3f0e36afd4a}

