---
layout: post
title:  Hack The Box Bucket writeup                             # Title of the page
hide_title: false                                  # Hide the title when displaying the post, but shown in lists of posts
feature-img: "/assets/img/Bucket_files/download.jpg"              # Add a feature-image to the post
thumbnail: "/assets/img/Bucket_files/download.jpg"   # Add a thumbnail image on blog view
color: dufault                            # Add the specified color as feature image, and change link colors in post
bootstrap: true                                   # Add bootstrap to the page
excerpt_separator: <!--more-->
tags: [HTB, writeup, Machines]
---
| Details |                     |
| ------------- |:-------------:|
| OS        | Linux           |
| Difficulty         | Medium     |
| Points      | 30    |


<br><!--more-->


<body lang=EN-US link=blue vlink=purple style='word-wrap:break-word'>

<div class=WordSection1>



<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<h2 style='margin:0in'><span style='font-family:"Calibri",sans-serif;color:#2E75B5'>Recon</span></h2>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>WithNmap, there are (80,22) are opened</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1241 height=355 id="Picture 1" src="/assets/img/Bucket_files/image001.jpg"></span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<h2 style='margin:0in'><span style='font-family:"Calibri",sans-serif;color:#2E75B5'>Bucket.htb : port 80</span></h2>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>
[!](assets/img/Bucket_files/image002.jpg)

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1349 height=723 id="Picture 2" src="assets/img/Bucket_files/image002.jpg" alt="002" "></span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>There is nothing to be useful, so let see the source to get more info</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1353 height=327 id="Picture 3" src="assets/img/Bucket_files/image003.jpg" alt="003"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Here is another subdomain to see, and there is nothing again</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=646 height=134 id="Picture 4" src="assets/img/Bucket_files/image004.jpg" alt="004"></span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Let's do some fuzzing:</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1287 height=399 id="Picture 5" src="assets/img/Bucket_files/image005.jpg" alt="005"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So starting with (shell) but there is something wrong, redirection to unknown host</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=566 height=179 id="Picture 6" src="assets/img/Bucket_files/image006.jpg"
alt="006"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>so we can test (\) to bypass this and it going to pass :D</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Here we go, AWS cloud with DynamoDB-JS-shell</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>  </span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1882 height=292 id="Picture 7" src="assets/img/Bucket_files/image007.jpg"
alt="007"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So we  can treat with this by AWC-CLI with AWS-DOC (</span><a
href="https://docs.aws.amazon.com/cli/latest/reference/dynamodb/"><span
style='font-size:14.0pt;font-family:"Calibri",sans-serif'>https://docs.aws.amazon.com/cli/latest/reference/dynamodb/</span></a><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'> , </span><a
href="https://docs.aws.amazon.com/cli/latest/reference/s3"><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>https://docs.aws.amazon.com/cli/latest/reference/s3</span></a><span
style='font-size:14.0pt;font-family:"Calibri",sans-serif'> , </span><a
href="https://docs.aws.amazon.com/cli/latest/reference/s3api"><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>https://docs.aws.amazon.com/cli/latest/reference/s3api</span></a><span
style='font-size:14.0pt;font-family:"Calibri",sans-serif'> )</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>First we need to configure it [aws configure] &gt;&gt; setting the key and region to anything but the output format to (table)</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Listing tables &gt;&gt; [ aws dynamodb list-tables --endpoint-url </span><a
href="http://s3.bucket.htb/"><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>http://s3.bucket.htb/</span></a><span
style='font-size:14.0pt;font-family:"Calibri",sans-serif'> ], then dump it with ( scan )</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=1021 height=646 id="Picture 8" src="assets/img/Bucket_files/image008.jpg" alt="008"></span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>But they aren't useful yet.</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So we need to think about any vulnerability leads to shell like RCE or file upload</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>After searching we found that there is a method to copy a file from our machine to
the server, and the uploaded files will been put in buckets </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So we need to know the bucket which we can upload the file to it, by [ aws s3api
list-buckets --endpoint-url </span><a href="http://s3.bucket.htb/"><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>http://s3.bucket.htb/</span></a><span
style='font-size:14.0pt;font-family:"Calibri",sans-serif'>] we found the bucket is ( adserver )</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So we can get our php-rev-shell from kali tool &gt; (
/usr/share/webshells/php-reverse-shell.php) or penetester mokey can help us,then uploading with [ aws s3 cp  rev.php s3://adserver.bucket.htb
--endpoint-url  </span><a href="http://s3.bucket.htb/adserver/"><span
style='font-size:14.0pt;font-family:"Calibri",sans-serif'>http://s3.bucket.htb/adserver/</span></a><span
style='font-size:14.0pt;font-family:"Calibri",sans-serif'>]</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Now we need to find from where we can execute this file, with [aws s3 ls
--recursive adserver --endpoint-url </span><a href="http://s3.bucket.htb/"><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>http://s3.bucket.htb/</span></a><span
style='font-size:14.0pt;font-family:"Calibri",sans-serif'>] we found that it is here (adserver.bucket.htb/rev.php)</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Testing
it with (s3.bucket.htb/rev.php) but there is nothing, so we can test from (bucket.htb/rev.php) and it is executed </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
border=0 width=759 height=207 id="Picture 9" src="assets/img/Bucket_files/image009.jpg" alt="009"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Now
with web shell, logically we search in web directories (/var/www/), we noticed (bucket-app/)
has Access-Control-List permisson</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=724 height=117 id="Picture 10" src="assets/img/Bucket_files/image010.jpg" alt="010"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So
now we can think about something else, we saw(/etc/passwd), we remembered the
foothold, we can test the passwords in the initial cred with the user ( roy ),
so we get into user, then into (bucket-app)</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>We found in it an unusually file (pd4ml.jar), which has an exploit lead to reading
file(https://medium.com/bugbountywriteup/how-i-hacked-redbus-an-online-bus-ticketing-application-24ef5bb083cd)</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>But we need root priv to get our root-files, by searching in files we found in (
index.php) some php code  </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=1896 height=603 id="Picture 11" src="assets/img/Bucket_files/image011.jpg" alt="011"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'> and
this file execute with root-priv </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=778 height=213 id="Picture 12" src="assets/img/Bucket_files/image012.jpg" alt="012"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>As
we can see from the code, it execute the injectable jar file and put the result
in ( var/www/bucket-app/files/result.pdf ) but in some condition:</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>1.
an post request with &quot;action&quot;=&quot;get_alerts&quot; so we need to
know on any port to send this request </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
border=0 width=1017 height=201 id="Picture 13" src="assets/img/Bucket_files/image013.jpg" alt="013"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>we
can send request with curl to the local host on port 8000 to see if that
(index.php) work on this port, and it send us a response, so this we want :D</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=858 height=313 id="Picture 14" src="assets/img/Bucket_files/image014.jpg" alt="014"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>2.
(table-name : alerts) and (title : ransomware) so we need to create it and
put   ( data ) with our payload </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>so
we can create a table and put item in the same code in the AWS-JS-shell from </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=1062 height=561 id="Picture 15" src="assets/img/Bucket_files/image015.jpg" alt="015"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>And
create our malicious JS-code and run it with the shell:</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'> </span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=782 height=598 id="Picture 16" src="assets/img/Bucket_files/image016.jpg"
alt="016 "></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Then
we do the post request with previous conditions [ curl -X POST -d
&quot;action&quot;=&quot;get_alerts&quot; localhost:8000 ]</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>With
our payload we get the private key of the root in ( result.pdf).</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=913 height=719 id="Picture 17" src="assets/img/Bucket_files/image017.jpg"
alt="017"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>get
it in our machine, then change its permission to (400) &gt; [ chmod 400
priv-key ]  then ssh with it by [ ssh  -i priv-key-file root@10.10.10.212 ]</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So
we now are the root :D</span></p>

</div>

</body>
