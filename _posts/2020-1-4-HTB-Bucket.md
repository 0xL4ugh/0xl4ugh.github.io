
---
layout: post
title:  Hack The Box Bucket writeup                             # Title of the page
hide_title: false                                  # Hide the title when displaying the post, but shown in lists of posts
feature-img: "assets/img/Bucket_files/download.jpg"              # Add a feature-image to the post
thumbnail: "assets/img/Bucket_files/download.jpg"   # Add a thumbnail image on blog view
color: dufault                            # Add the specified color as feature image, and change link colors in post
bootstrap: true                                   # Add bootstrap to the page
excerpt_separator: <!--more-->
tags: [HTB, writeup, Machines]
---
<p style='margin:0in'><span style='font-size:20.0pt;font-family:"Calibri Light",sans-serif'>Bucket-writeup</span></p>

<p style='margin:0in'><span style='font-size:10.0pt;font-family:"Calibri",sans-serif;color:#767676'>Monday, January 4, 2021</span></p>

<p style='margin:0in'><span style='font-size:10.0pt;font-family:"Calibri",sans-serif;color:#767676'>4:31 PM</span></p>

<p style='margin:0in'><span style='font-size:13.0pt;font-family:"Calibri",sans-serif'>OS: <span style='color:#201F1E'>Linux</span></span></p>

<p style='margin:0in'><span style='font-size:13.0pt;font-family:"Calibri",sans-serif'>Difficulty: Medium</span></p>

<p style='margin:0in'><span style='font-size:13.0pt;font-family:"Calibri",sans-serif'>Points: 30</span></p>
<br><!--more-->


<body lang=EN-US link=blue vlink=purple style='word-wrap:break-word'>

<div class=WordSection1>



<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<h2 style='margin:0in'><span style='font-family:"Calibri",sans-serif;color:#2E75B5'>Recon</span></h2>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>WithNmap, there are (80,22) are opened</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1241 height=355 id="Picture 1" src="assets/img/Bucket_files/image001.jpg"></span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<h2 style='margin:0in'><span style='font-family:"Calibri",sans-serif;color:#2E75B5'>Bucket.htb : port 80</span></h2>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1349 height=723 id="Picture 2" src="assets/img/Bucket_files/image002.jpg"
alt="Bucket Advertising &#10;Customize Ads that suits &#10;to your business &#10;Contact us on &#10;support@bucket.htb &#10;Mob: +1 0011223344 &#10;Platform &#10;Home &#10;Bug Bounty and Oday Research &#10;MARCH 17. 2020 | SECURITY &#10;About &#10;Customised bug bounty and new Oday feeds. Feeds can be used on TV. &#10;mobile. desktop and web applications. Collecting security feeds from &#10;100+ different trusted sources around the world. &#10;Ransomware Alerts &#10;MARCH 17, 2020 | MALWARE &#10;Run awareness ad campaigns on Ransomwares and other newly found &#10;malwares. Choose different types Of malwares to fit for your campaign &#10;Cloud Updates &#10;MARCH 17, 2020 | CLOUD &#10;Stay tuned to cloud technology updates. A superior alternative to push &#10;Notifications and SMS A2P alerts. "></span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>There is nothing to be useful, so let see the source to get more info</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1353 height=327 id="Picture 3" src="assets/img/Bucket_files/image003.jpg"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Here is another subdomain to see, and there is nothing again</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=646 height=134 id="Picture 4" src="assets/img/Bucket_files/image004.jpg" alt="{&quot;status &#10;s 3, bLKket,htb &#10;&quot;running&quot; "></span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Let's do some fuzzing:</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1287 height=399 id="Picture 5" src="assets/img/Bucket_files/image005.jpg"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So starting with (shell) but there is something wrong, redirection to unknown host</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=566 height=179 id="Picture 6" src="assets/img/Bucket_files/image006.jpg"
alt="444af2S0749dA506'shcLL; &#10;CrockStation - O G) &#10;Burp suite community Edition &#10;Error &#10;unknown host; 444af250749d "></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>so we can test (\) to bypass this and it going to pass :D</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Here we go, AWS cloud with DynamoDB-JS-shell</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>  </span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=1882 height=292 id="Picture 7" src="assets/img/Bucket_files/image007.jpg"
alt="• amazon &#10;web ser vices &#10;DynamoDB JavaScript Shell &#10;Welcome to the DynamoDB Web Shell &#10;Get started with some API templates by clicking the button on the menu screen or &#10;tutorial by typing in t (l • &#10;Or take a getting tour: &#10;start the "></span></p>

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

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=1021 height=646 id="Picture 8" src="assets/img/Bucket_files/image008.jpg"></span></p>

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
border=0 width=759 height=207 id="Picture 9" src="Bucket_files/image009.jpg"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Now
with web shell, logically we search in web directories (/var/www/), we noticed (bucket-app/)
has Access-Control-List permisson</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img border=0 width=724 height=117 id="Picture 10" src="assets/img/Bucket_files/image010.jpg"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So
now we can think about something else, we saw(/etc/passwd), we remembered the
foothold, we can test the passwords in the initial cred with the user ( roy ),
so we get into user, then into (bucket-app)</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>We found in it an unusually file (pd4ml.jar), which has an exploit lead to reading
file(https://medium.com/bugbountywriteup/how-i-hacked-redbus-an-online-bus-ticketing-application-24ef5bb083cd)</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>But we need root priv to get our root-files, by searching in files we found in (
index.php) some php code  </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
border=0 width=1896 height=603 id="Picture 11" src="assets/img/Bucket_files/image011.jpg"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'> and
this file execute with root-priv </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
border=0 width=778 height=213 id="Picture 12" src="assets/img/Bucket_files/image012.jpg"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>As
we can see from the code, it execute the injectable jar file and put the result
in ( var/www/bucket-app/files/result.pdf ) but in some condition:</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>1.
an post request with &quot;action&quot;=&quot;get_alerts&quot; so we need to
know on any port to send this request </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
border=0 width=1017 height=201 id="Picture 13" src="assets/img/Bucket_files/image013.jpg"
alt="State &#10;LISTEN &#10;LISTEN &#10;LISTEN &#10;LISTEN &#10;LISTEN &#10;LISTEN &#10;LISTEN &#10;roy@bucket : /var/wvm/bucket-app$ ss -ntl &#10;127 . 0.0. 53810 : 53 &#10;127.0. o &#10;127.0.0.1:8000 &#10;Recv-o &#10;O &#10;o &#10;send-o &#10;4096 &#10;4096 &#10;128 &#10;511 &#10;4096 &#10;128 &#10;511 &#10;Local Address:Port &#10;.1:4566 &#10;Add ress : PO rt &#10;0.0. o &#10;0.0. o &#10;o &#10;. 0.0 &#10;0.0. o &#10;0.0. o &#10;Proces "></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>we
can send request with curl to the local host on port 8000 to see if that
(index.php) work on this port, and it send us a response, so this we want :D</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
border=0 width=858 height=313 id="Picture 14" src="assets/img/Bucket_files/image014.jpg"></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>2.
(table-name : alerts) and (title : ransomware) so we need to create it and
put   ( data ) with our payload </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>so
we can create a table and put item in the same code in the AWS-JS-shell from </span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
border=0 width=1062 height=561 id="Picture 15" src="assets/img/Bucket_files/image015.jpg"
alt="amazon &#10;web services &#10;API Templates &#10;Putltenn &#10;updateltem &#10;Deleteltem &#10;BatchVMriteltem &#10;Getltem &#10;BatchGetltem &#10;Query &#10;Scan &#10;Create Table "></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>And
create our malicious JS-code and run it with the shell:</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'> </span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
border=0 width=782 height=598 id="Picture 16" src="assets/img/Bucket_files/image016.jpg"
alt="zon &#10;rvices &#10;DynamoDB . &#10;- var pa rams &#10;KeySchema: I &#10;/ / Requi red HASH &#10;type attribute &#10;At t r ibu teName : &#10;•title', &#10;Key Type HASH • , &#10;Att rlbuteDeT1n1t10ns: [ &#10;AttributeName: title' , &#10;more attributes &#10;ProvisionedTh roughput : &#10;WriteCapacI : &#10;requi red &#10;p sloned &#10;th roughput &#10;for &#10;the &#10;table &#10;20 &#10;22 &#10;26 &#10;27 &#10;33 &#10;34 &#10;37 &#10;dynamodb c ( data) &#10;if (err) ppJson(err); &#10;// an error occurred &#10;else ppjson : // response &#10;Var pa rams &#10;TableName : &#10;•alerts', &#10;Item: &#10;&quot;title&quot;: &#10;&quot;data&quot; : &#10;&quot;epd4mt :attachment description— attached. txt ' &#10;/ . id_ : attachment*&quot; &#10;. put ( params. function ( err, data) &#10;it (err) ppJson(err); &#10;// an error occurred &#10;else ppJson(data); // success Tul response &#10;Icon— &#10;• Pushpin ' "></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>Then
we do the post request with previous conditions [ curl -X POST -d
&quot;action&quot;=&quot;get_alerts&quot; localhost:8000 ]</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>With
our payload we get the private key of the root in ( result.pdf).</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
border=0 width=913 height=719 id="Picture 17" src="assets/img/Bucket_files/image017.jpg"
alt="- -BEGIN OPENSSH PRIVATE KEY-- &#10;b3B1 1 ax k t d j EAAAAABG5Vbmt_JAAAAEbmguZQAAAAAAAAABAAABIWAAAAdZC2qtc r &#10;NhAAAAAwEAAQAAAY EAx6VphKMyxu r j dmb6dy10SnOD9dumFAUCeSoICwhhsq+ fadx21 S L &#10;bo r/ uno f K rmgNMAhj m rHC iMapmDw1dcy j 4 PSPtw061v r VOGuyu34Law1 Ea v9sV1 h g z D Lmt &#10;9tAB7fh2JN80B/ &#10;IVtctPCOi6*CMCV11MVdFtBLbieffTAOF1rSJdS4mOOMpqQWDiQdqN50hCOLIbTXf3Cbj z q &#10;uCTBtX02dcLfHAqhqYSa7eMOx5pwX54Hr9SPOqJp5yOueraiOdoSJD5SmgBf1fCzUDZAMr &#10;de 3YGZ004a 86 B V g s D 2 V 54±9 ho LOYMs i V9g4S 7 6+PrnBi uwi/W rx t o y z r-3/ htJVmCpm+Wf &#10;r400ZyCFAV021sLf u r5Fv rWtUUCAOus f x/ j 40V/ &#10;1+d/BXAONVYt/ aoennafqvzs j rlUsuqYFLAAAAB3NzaC1ycz• &#10;EAAAGBAMe a Y S j Ms bq 4 5 X Zm+ n c t Tk p9A/ X b phOFAn kq C As I YbKvn2n cd t U GOK/ 7 p6Hyq &#10;oDTAI Y 5qxwo j GqZg8NXXM0+DO j 7 c KO i L 6 IdB rs rt+C2sNRG r/ b F dYYMwy5 vPbOAe34diT t &#10;Dgf +HbdLF s R8c InwphxeOwVkpcXZPi u B9 ryfnkwNhcU9 rXiz5iXexvZ r2p4dVbXLaOj o u \ &#10;q j HL9SDL3RbQS24nn30WDhdaOiXbOJ &#10;3xwKoamEmu 3 j NMea c F B6/ U j 9K i ae c t Lnq 2 0 j na E i O+IJ poAXyHws IA2 QDJ 3Xt2 Brnd EOG•v &#10;OgVY LA91 Zee PvYaC zmDLI L f YOEu+v j 5gY r sIv1 q8baMs69/ 4bSVZgqZvInzq+EEGcghOF &#10;NtbC3YKj HDwapbqtRb61 rVFAgNL rH8f4+NFf5eVgC1qCDt9F5U9JJZdXtj+9fnfwVWEDbE &#10;rOVf6YtUtPsPE &#10;vd i I OMRpq+tw3mdsnOXX2 k r50myTX1gEv HP4MG4 PVmqg5 ZaxbONmmZNoTkj t Pc TvUeF 5 T &#10;3mhaJ z uR rFws ZJ9kVXwgE7 sqG8+x/ F4gR IAq s 4NG t Hnu0603gn OwvONKUd yRMd+dm/ -YVE &#10;fSj r nayOffTWY*JQ2fU5AGPbYBk+mwuYUOVWOOCCSKSk8WdiOWN , &#10;myKP+DhCGmgo j 7F6ysmqfnWRS66072L70 &#10;c VD ze568Zmdw ryyVu+HD oy cWq iw5 z VenX18 c 3 h q9AHu E CwRqY z / c / ZmqwOo n ZzOm8P8Z &#10;S4SLA1 f rFVOf r08TEPTeBmKCOBbKYCbyvU1mPZTOJV+BexgMF8CfXiCkDGXCX7XLIVTOAA &#10;AMEAIZDX+SRb4BUkEYVP02n/GV8GV0251ZCRMfNbWERwzeZ6uf92eC050LfTKHYh0Z8WBC_ &#10;npypo LIEjwiBOPybH9W12TrSquC16d2sUwWJ rkQ11CTPIX5WMFdwsOj015S: &#10;44Sj &#10;4 IOD j NCF j aQSVMTWkA nAAAAwOD j 010 rxsxxqzt ; &#10;fSZTTPNaNB+e+K11X06EkhH480FVRnFPLCCJCX/H5uEHBtEXRuyaPkUYVt85h4e1QN61b, &#10;KZs9p2b4kH/ cF8+BFj 105J r4z6XetJ f h072gYW, &#10;EtZFCf5Z4Q4ta ryZQYYPXUEOPTXPABbrnnOjOQ6CIMtTnJh0Af/THSKnSGb8RABLXG/KSAt &#10;ltOoT70NTv2gFGWAb6WHLEByEsnYOwk5ynb1btaApQSZEyVEPkf9Lm07AEb081VAOSOdO] &#10;XMYLerifOCNjmemWAAAAtYb290QHV idW50dOECAWOFBg-- "></span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>get
it in our machine, then change its permission to (400) &gt; [ chmod 400
priv-key ]  then ssh with it by [ ssh  -i priv-key-file root@10.10.10.212 ]</span></p>

<p style='margin:0in'><span style='font-size:14.0pt;font-family:"Calibri",sans-serif'>So
we now are the root :D</span></p>

</div>

</body>
