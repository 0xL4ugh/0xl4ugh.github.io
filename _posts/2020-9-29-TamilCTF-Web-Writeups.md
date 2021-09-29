---
layout: post
title: TamilCTF 2021 Web Challenges Writeups                               # Title of the page
hide_title: false                                  # Hide the title when displaying the post, but shown in lists of posts
feature-img: "assets/img/writeups/tamilctf2021/Screenshot_2.png"              # Add a feature-image to the post
thumbnail: "assets/img/writeups/tamilctf2021/Screenshot_2.png"  # Add a thumbnail image on blog view
color: dufault                            # Add the specified color as feature image, and change link colors in post
bootstrap: true                                   # Add bootstrap to the page
author: abdoghazy
excerpt_separator: <!--more-->
tags: [ctf, writeup, Web]
---
<h1>TamilCTF 2021 Web Challenges Writeups </h1>  
 <!--more-->


hello everybody iam abdelhameed ghazy and this is my writeup for web challenges in tamilctf 2021 


First Challenge : CringeNcoder (scripting)
Des : flag is located at flag, but its not flag

when you enter the challenge we will find this :
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_2.png" />
as you see from the challenge name and this page we noticed it's an encoder so let's try it 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_4.png" />
as you see when i enter "a" i got some word and when i entered "ab" i got these two words 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_5.png" />
then i go to /flag to see what's on it 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_3.png" />
it's clear now we had an encoded flag and an encoder and they allowed us to use only lowercase chars and numbers 
we could made it manually but i prefered to auomate the process
so i made this script : 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_63.png" />
the flaw of my script is taking every encoded word and try to get the encoded value for every chars and numbers we will use if the encoded value equal to the cipher add the char to the flag
first i imported python requests library 
**note that i imported sys by wrong no need to it **
then i declared a string variable called flag to store flag on it 
then stored all need chars and numbers in varibale called alpha
and the cipher in variable called cipher
then i looping in the cipher and take every word and stored it in var called g then i for looped in alpha and then looping in the first loop to send post request to encode every char
and then check if the encoded value in cipher equal to the encoded value in the request if equal just add the char to the flag  and got this result
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_16.png" />

Seconde Challenge : it's paid (e-shop logic bug & leaked creds)
Des : I heard that admin leaked something somewhere o.O

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_6.png" />

as we see it's a online courses platform nothing intersted in the home page so i navigated to the courses page 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_7.png" />
when you enter any course you will find this page
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_8.png" />
i tried sqli in reddem code parameter to bypass it or to dump data but i couldn't
so i tried to buy the course and intercept the request 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/tamilctf2021/Screenshot_9.png" />
as you see at the request the bug here is the price sent from client-side so let's try to manuplate it maybe it's not validated in server-side so i made the prize 0 to made it free
10-------
and Alhamdullah as you see it's working !!!
11-------
when i entered every course i noticed that every course had 2 seconds video told us it will be available next batch i keep doing this until i found a 10 seconds video so i started this video and found admin panel,creds as a plain text in the url !!!
12--------
so i navigated into the panel and logged in by the creds and i found this 
13-------
then i noticed that i had cookie called special person had false value
14------
so i made it true and got the flag Hamdullah
15------


Third Challenge : Open Flag (ssti & upload from terminal)

17-----

as you see there is a login panel i tried sqli on it but nothing interested 
so i tried to register manually and intercept the request to play with it 
19------
as you see there my username reflected on the source as a html comment so and because it's a post request i will let the xss to the end and also from webapplizer we will know the server uses flask so i tried ssti (server side template injection ) so i tried {{7*7}} to check and alhamdullah it's working 
20------
so i opened this repo to get ssti payloads 
(https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server Side Template Injection)
then i used this payload and it's working also Hamdullah 
21------

as you see in the same page source the flag is in flag.jpg so i used (which curl)
command to make sure that the curl is installed in the system then i used 
transfer.sh site to upload the photo 
22------

and this is the flag Hamdullah ! 
24---------


Fourth Challenge : Recovery (OTP breach leads to bypass)
des: Help PJ pls, he is a memory loss patient who forgot his password Try your hacking skills to help him

25---------------

as you see the home page had 2 tabs 
when we enter Solve The Challenge we will found login page
32------
no bypass,no sqli so i cameback and entered Help PJ 
and i found a reset password form contains mail and lastpassword and capatcha i found last password in html comment :
<!-- i think it's tamilctf123 -->
27-----
after i filled the form i found an otp enter so i asked the admin if there is any bruteforcing and he told me no bruteforcing 
so as usual i tried sqli and searching for any leaked data 
and also there is no response manuplation or host header injection so let's cameback and trace the request of resetting password after i intercept the request i found the otp breached at response header for the reset request 

29------

so i submitted it and site redirected me to this page 
30----
after i veiewd the sourcecode i found i hidden tag with a cookie name and value so i set it and after that i cameback to solve the challenge and i found the form had no action and there is a comment told us that "/login" is missing here so when i entered /login i found the flag in the source  
33------

Fifth Challenge : News Letter (sqli leads to bypass login , xxe )
des:TamilCTF plans to send news updates to their participants, a web developer from their team creates a Web App for that. You have been informed to steal the flag from their Web App.

34-----

there is a login form with header told us to breah the auth
so i used 
' or 1=1 limit 1 #
and i bypassed it hamdullah 
then it redirected me to signup form for newsletter 
i tried sqli also xD (always trying it in every place i feel it's dealing with db ) it's not vulnerable to sqli so i filled the form and found that the email reflected in the page told is that's exist before so i tried random emails and response is static just the email changes 
35-------
after viewing the source i found that the form sends by xml request in xml form so i intercepted the request and found this 
36-----
after that i opened this repo :
https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/XXE%20Injection
and tried xxe and it worked so i treid to read /etc/passwd file 
37--------------
after that i read the source of the php files
38-------
but no flag also 
but after viewing the html source i found this html comment:
<!--Your "flag" is in the directory which stores configuration files-->
so i tried to read "/etc/flag"
and found the flag Hamdullah 3>
39----------

Sixth Challenge : Meeting (mix of things xD)
des:Gokul is trying to cheat in this test, Help him

40

as we see maybe it's a video meetings paltform 
i tried to get sqli or to bypass meetcode parameter but it's not vulnerable to it so i trying to get a new meeting code but it's sending get request to the same page so i tried to send post request and i get a base64 encoded meeting code 
41-------
after i decoded it and enter the meeting i found that i cannot send anything to the meeting chat and also i logged in as (jopraveen) user and as we know from challenege description we need to be Gokul to help him cheating xD
42-------- 
so i see the cookies to see how it's set our user and i found cookie called user that controls this 
43-----------
so i changed it to Gokul and now we are logged in with his account
44--------
as you can see we could send in the meeting chat 
so i tried xss and ssti but there is no thing interested 
so i viewed the source code and found this html comment :
<!-- Note: If you send a link here Exploit Everything will open it-->

so i put my beeceptor link and recieved a request 
and while i see the request headers i see this 
45--------
yeah , it's admin cookie so i set it and found magic word appeared but i didn't know how to use it
so i watch the meeting video and found that the exam is in /form 
47----------
so i opened it and filled it with the magic word and got the flag and also first blood Alhamdullah 3>
48----------------

Seventh Challenge : become admin (host header injection )
Des : I heard you’re a hacker can you become admin of this site ?

49---------------

they provide creds of admin and told you that db was removed due to cyber attack so let's try to login with the creds
51-------
no thing here but i noticed that the path we are in is /account/login 
52-------
so i tried /account/register and it's worikng ;)
53----------
i registered by the creds like the title said and resirected to the dashboard 
54-------------
but once i clicked on get the flag it was a trick kicked us out :/
55-----
and we are now in this page 
56--------
it said that the admin automate his password resetting so let's try to reset password and intercept the request 
57-----
nothing breached so i tried host header injection attack 
59----------
as you see i edited the host header with my beeceptor and recieved the token Hamdullah 3>
58-----------
after i navigated to the token i could change the password of admin now
60---------
after i send the request i found the flag in the response header 
61------------

