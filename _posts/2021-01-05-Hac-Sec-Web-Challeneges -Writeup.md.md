---
layout: post
title: Hac-Sec 2021 Web Challenges Writeup                               # Title of the page
hide_title: false                                  # Hide the title when displaying the post, but shown in lists of posts
feature-img: "assets/img/writeups/hac-sec/Hac_Security.png"              # Add a feature-image to the post
thumbnail: "assets/img/writeups/hac-sec/Hac_Security.png"  # Add a thumbnail image on blog view
color: dufault                            # Add the specified color as feature image, and change link colors in post
bootstrap: true                                   # Add bootstrap to the page
author: Abdelhameed Ghazy
excerpt_separator: <!--more-->
tags: [ctf, writeup, Web]
---
Hac-Sec 2021 Web Challenges Writeup  
 <!--more-->


Hello Every One, I hope all is well with you :) 
Iam Abdelhameed Ghazy A Member OF 0xL4ugh Team 3> and there is my writeup for all web challenges in HAC-SEC CTF 
In Fact The Web challenges Was So Easy And The Last one Is amazing 3> 

The First challenge called easy and when you open the link and view the source and search for the flag format you will find it :) 
<img src="assets/img/writeups/hac-sec/easy.png"/>


The Second challenge Called guess and when you entered it you will see that :

<img src="assets/img/writeups/hac-sec/guess.png" />

so let's give it a get parameter called guess 
assets/img/writeups/hac-sec/guess1.png
as you see alhamdullah we are in the right path :) 
so to show the flag we must give guess parameter a number  with this conditions :
1- greater than 2000 
2- it's hexadecimal is greater than AF0 Which Equal 2800
3- it's binary equal 101011111001 (2809) 
so let's get the flag by 2809 


The Third Challenge Called Wish As I remembered 
when you entered the challenge it  was a race xD
you will see that you are in a loop redirected from 1.php to 18.php
and every page print single character so let's intercept the request
with burp suite and see each single page like that :
assets/img/writeups/hac-sec/wish.png
so after collect the 17 part of the flag we will see that's 
a fake flag :) but the good thing that we find at 14.php
there is a base64 comment
assets/img/writeups/hac-sec/wish1.png
so after decoding it  we will get :
(/genie.php grants anything that you "wish" for)
so let's open the genie.php and give him or wish (flag) :) 
after visit genie.php?wish=flag it will give us
assets/img/writeups/hac-sec/wish2.png
so let's give it a key parameter and also it must have some rules :
1- it must be a number 
2- maximum length is 3 
3- more than 9999 and it's must be more than 999
so lst's try exponential :)  and we will git flag at 9e3



The Forth Challenge and the Amazing One is Called Include :) 
when we enter it we will see a button and when we click on it
it will set get parameter called view with a value 
("/var/www/html/") and prints some words in the page
<img src="assets/img/writeups/hac-sec/include.png" />
so from the challenge name  and the parameter view
we will understand that we are in LFI Challenge
after trying much payloads and no thing worked :(
but i recognized that there is a filter shown an error  
so i decided to get back and understand the challenge logic 
i tried to put normal characters and numbers in the view parameter 
but it also give us an error so  i understand that there is a validation
for /var/www/html so the first thing i thinked is to include the logs of the apache server
and put our php code there but for sorry i couldn't 
then i tried to upload the php code in my site and include it 
so i upload a file in http://abdelhameedghazy.com/var/www/html/abdo.txt
and alhamdullah there is no error but also there is no output 
so let's get back again and try to see the source of the file by using php wrappers
and alhamdullah i could get the souce by this payload : 
php://filter/convert.base64-encode/resource=/var/www/html/index
<img src="assets/img/writeups/hac-sec/include1.png"/>
after doing some code review i understand that there is another 
get parameter called ext when it's not set the extention of the file will be php
and when it exist it the value will be the extention of the file  
so now i know why when i try to include from my website it didn't work 
so let's put it and do path traversal to get the flag 
our payload becomes : 
?view=/var/www/html&ext=../../../../../../etc/flag
the location of the flag is in robots.txt :)  
