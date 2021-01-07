---
layout: post
title: HAC-SEC Reprisal Write up                          # Title of the page
hide_title: false                                  # Hide the title when displaying the post, but shown in lists of posts
feature-img: "/assets/img/Reprisal_files/logo.jpg"              # Add a feature-image to the post
thumbnail: "/assets/img/Reprisal_files/logo.jpg"  # Add a thumbnail image on blog view
color: dufault                            # Add the specified color as feature image, and change link colors in post
bootstrap: true                                   # Add bootstrap to the page
author: xElessaway
excerpt_separator: <!--more-->
tags: [ctf, writeup, DigitalForensics]
---
This is the Digital forinsces challenge Reprisal writeup for the HAC-SEC CTF2021
<br><!--more-->

| Details |                     |
| ------------- |:-------------:|
| Points        | 300           |
| Category      | Digital Forensics     |

<div class=WordSection1>



<p class=MsoNormal align=center style='text-align:center;line-height:11.55pt'><span
style='mso-ascii-font-family:Calibri;mso-fareast-font-family:"Times New Roman";
mso-hansi-font-family:Calibri;mso-bidi-font-family:Calibri;color:black'><o:p>&nbsp;</o:p></span></p>

<p class=MsoNormal style='mso-line-height-alt:11.55pt'><span style='font-size:
18.0pt;font-family:"Abd ElRady";mso-fareast-font-family:"Times New Roman";
color:black'>Okay first I download the file and it was&nbsp;<span class=SpellE>pcap</span>&nbsp;<span
class=GramE>file</span>&nbsp;so I opened it and went through&nbsp;<span
class=SpellE>tcp</span>&nbsp;streams till I found stream 4 include zip file
header and file name called = “da_op_files.zip”<o:p></o:p></span></p>

<p class=MsoNormal style='line-height:11.55pt'><span style='mso-ascii-font-family:
Calibri;mso-fareast-font-family:"Times New Roman";mso-hansi-font-family:Calibri;
mso-bidi-font-family:Calibri;color:black'><o:p>&nbsp;</o:p></span></p>

<p class=MsoNormal><span style='mso-no-proof:yes'><img border=0
src="/assets/img/Reprisal_files/image001.jpg" v:shapes="Picture_x0020_1"></span></p>

<p class=MsoNormal style='mso-line-height-alt:11.55pt'><span style='font-size:
18.0pt;font-family:"Abd ElRady";mso-fareast-font-family:"Times New Roman";
color:black'><o:p>&nbsp;</o:p></span></p>

<p class=MsoNormal style='mso-line-height-alt:11.55pt'><span style='font-size:
18.0pt;font-family:"Abd ElRady";mso-fareast-font-family:"Times New Roman";
color:black'><o:p>&nbsp;</o:p></span></p>

<p class=MsoNormal style='mso-line-height-alt:11.55pt'><span style='font-size:
18.0pt;font-family:"Abd ElRady";mso-fareast-font-family:"Times New Roman";
color:black'><o:p>&nbsp;</o:p></span></p>

<p class=MsoNormal style='mso-line-height-alt:11.55pt'><span style='font-size:
18.0pt;font-family:"Abd ElRady";mso-fareast-font-family:"Times New Roman";
color:black'><o:p>&nbsp;</o:p></span></p>

<p class=MsoNormal style='mso-line-height-alt:11.55pt'><span class=GramE><span
style='font-size:18.0pt;font-family:"Abd ElRady";mso-fareast-font-family:"Times New Roman";
color:black'>So</span></span><span style='font-size:18.0pt;font-family:"Abd ElRady";
mso-fareast-font-family:"Times New Roman";color:black'>&nbsp;I extracted this
file by using network miner</span><span style='mso-ascii-font-family:Calibri;
mso-fareast-font-family:"Times New Roman";mso-hansi-font-family:Calibri;
mso-bidi-font-family:Calibri;color:black'><o:p></o:p></span></p>

<p class=MsoNormal><span style='mso-no-proof:yes'><img border=0 src="/assets/img/Reprisal_files/image003.jpg" v:shapes="Picture_x0020_2"></span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady";color:black'>I tried to extract it but it had password so I tried
to use john on it but nothing so I back to&nbsp;</span><span class=SpellE><span
class=spelle><span style='font-variant-ligatures: normal;font-variant-caps: normal;
orphans: 2;text-align:start;widows: 2;-webkit-text-stroke-width: 0px;
text-decoration-thickness: initial;text-decoration-style: initial;text-decoration-color: initial;
word-spacing:0px'>tcp</span></span></span><span style='font-variant-ligatures: normal;
font-variant-caps: normal;orphans: 2;text-align:start;widows: 2;-webkit-text-stroke-width: 0px;
text-decoration-thickness: initial;text-decoration-style: initial;text-decoration-color: initial;
float:none;word-spacing:0px'>&nbsp;streams again and I found the password on
the 5th</span><sup style='font-variant-ligatures: normal;font-variant-caps: normal;
orphans: 2;text-align:start;widows: 2;-webkit-text-stroke-width: 0px;
text-decoration-thickness: initial;text-decoration-style: initial;text-decoration-color: initial;
word-spacing:0px'><span style='font-family:"Abd ElRady";color:black'>th</span></sup><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady";color:black'><span
style='font-variant-ligatures: normal;font-variant-caps: normal;orphans: 2;
text-align:start;widows: 2;-webkit-text-stroke-width: 0px;text-decoration-thickness: initial;
text-decoration-style: initial;text-decoration-color: initial;float:none;
word-spacing:0px'>&nbsp;stream and it was =&nbsp;</span><span class=GramE><span
class=grame><span style='font-variant-ligatures: normal;font-variant-caps: normal;
orphans: 2;text-align:start;widows: 2;-webkit-text-stroke-width: 0px;
text-decoration-thickness: initial;text-decoration-style: initial;text-decoration-color: initial;
word-spacing:0px'>“ 4</span></span></span><span style='font-variant-ligatures: normal;
font-variant-caps: normal;orphans: 2;text-align:start;widows: 2;-webkit-text-stroke-width: 0px;
text-decoration-thickness: initial;text-decoration-style: initial;text-decoration-color: initial;
float:none;word-spacing:0px'>lls4f3s3cur1ty ”</span><o:p></o:p></span></p>

<p class=MsoNormal><span style='mso-no-proof:yes'><img border=0 
src="/assets/img/Reprisal_files/image005.jpg" v:shapes="Picture_x0020_3"></span></p>

<p class=MsoNormal><span class=GramE><span class=grame><span style='font-size:
18.0pt;line-height:107%;font-family:"Abd ElRady";color:black'>So</span></span></span><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady";color:black'><span
style='font-variant-ligatures: normal;font-variant-caps: normal;orphans: 2;
text-align:start;widows: 2;-webkit-text-stroke-width: 0px;text-decoration-thickness: initial;
text-decoration-style: initial;text-decoration-color: initial;word-spacing:
0px'>&nbsp;I extracted data and I got 1 pdf and 1&nbsp;<span class=SpellE><span
class=spelle>pcap</span></span>&nbsp;file so I checked the&nbsp;<span
class=SpellE><span class=spelle>pcap</span></span>&nbsp;file but nothing
interesting in it so I tried if there is any tool to crack pdf password</span><o:p></o:p></span></p>

<p class=MsoNormal><span style='mso-no-proof:yes'><img 
src="/assets/img/Reprisal_files/image006.jpg" v:shapes="Picture_x0020_4"></span></p>

<p class=MsoNormal style='mso-line-height-alt:11.55pt'><span class=GramE><span
style='font-size:18.0pt;font-family:"Abd ElRady";mso-fareast-font-family:"Times New Roman";
color:black'>so</span></span><span style='font-size:18.0pt;font-family:"Abd ElRady";
mso-fareast-font-family:"Times New Roman";color:black'>&nbsp;I found that there
is pdf2john.pl</span><span style='mso-ascii-font-family:Calibri;mso-fareast-font-family:
"Times New Roman";mso-hansi-font-family:Calibri;mso-bidi-font-family:Calibri;
color:black'><o:p></o:p></span></p>

<p class=MsoNormal style='mso-line-height-alt:11.55pt'><span style='font-size:
18.0pt;font-family:"Abd ElRady";mso-fareast-font-family:"Times New Roman";
color:black'>So I tried it and I got the password =&nbsp;<span class=GramE>“&nbsp;<span
class=SpellE>ihatehackers</span></span>&nbsp;”</span><span style='mso-ascii-font-family:
Calibri;mso-fareast-font-family:"Times New Roman";mso-hansi-font-family:Calibri;
mso-bidi-font-family:Calibri;color:black'><o:p></o:p></span></p>

<p class=MsoNormal><span style='mso-no-proof:yes'><img 
src="/assets/img/Reprisal_files/image007.jpg" v:shapes="Picture_x0020_5"></span></p>

<p class=MsoNormal><o:p>&nbsp;</o:p></p>

<p class=MsoNormal><o:p>&nbsp;</o:p></p>

<p class=MsoNormal style='mso-line-height-alt:11.55pt'><span class=GramE><span
style='font-size:18.0pt;font-family:"Abd ElRady";mso-fareast-font-family:"Times New Roman";
color:black'>So</span></span><span style='font-size:18.0pt;font-family:"Abd ElRady";
mso-fareast-font-family:"Times New Roman";color:black'>&nbsp;it’s looks like
base64</span><span style='mso-ascii-font-family:Calibri;mso-fareast-font-family:
"Times New Roman";mso-hansi-font-family:Calibri;mso-bidi-font-family:Calibri;
color:black'><o:p></o:p></span></p>

<p class=MsoNormal><span style='mso-no-proof:yes'><img 
src="/assets/img/Reprisal_files/image008.jpg" v:shapes="Picture_x0020_6"></span></p>

<p class=MsoNormal style='mso-margin-top-alt:auto;mso-margin-bottom-alt:auto;
line-height:normal;background:white'><span style='font-size:18.0pt;font-family:
"Abd ElRady";mso-fareast-font-family:"Times New Roman";color:#262626'>So, I can
see that it’s <span class=SpellE>png</span> from the header and <span
class=GramE>footer</span></span><span style='font-size:15.0pt;font-family:"Source Sans Pro",sans-serif;
mso-fareast-font-family:"Times New Roman";mso-bidi-font-family:"Times New Roman";
color:#262626'><o:p></o:p></span></p>

<p class=MsoNormal><span style='mso-no-proof:yes'><img 
src="/assets/img/Reprisal_files/image009.jpg" v:shapes="Picture_x0020_7"></span></p>

<p class=MsoNormal style='mso-margin-top-alt:auto;mso-margin-bottom-alt:auto;
line-height:normal;background:white'><span style='font-size:18.0pt;font-family:
"Abd ElRady";mso-fareast-font-family:"Times New Roman";color:#262626'><o:p>&nbsp;</o:p></span></p>

<p class=MsoNormal style='mso-margin-top-alt:auto;mso-margin-bottom-alt:auto;
line-height:normal;background:white'><span style='font-size:18.0pt;font-family:
"Abd ElRady";mso-fareast-font-family:"Times New Roman";color:#262626'><o:p>&nbsp;</o:p></span></p>

<p class=MsoNormal style='mso-margin-top-alt:auto;mso-margin-bottom-alt:auto;
line-height:normal;background:white'><span style='font-size:18.0pt;font-family:
"Abd ElRady";mso-fareast-font-family:"Times New Roman";color:#262626'>So, after
I used it wow <span class=GramE>it’s</span> corrupted!!!</span><span
style='font-size:15.0pt;font-family:"Source Sans Pro",sans-serif;mso-fareast-font-family:
"Times New Roman";mso-bidi-font-family:"Times New Roman";color:#262626'><o:p></o:p></span></p>

<p class=MsoNormal><span style='mso-no-proof:yes'><img border=0 
src="/assets/img/Reprisal_files/image010.jpg" v:shapes="Picture_x0020_9"></span></p>

<p class=MsoNormal><span class=GramE><span style='font-size:18.0pt;line-height:
107%;font-family:"Abd ElRady";color:#262626;background:white'>So</span></span><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady";color:#262626;
background:white'> I started to fix it and boom the flag:<o:p></o:p></span></p>

<p class=MsoNormal><span style='mso-no-proof:yes'><img border=0 
src="/assets/img/Reprisal_files/image011.jpg" v:shapes="Picture_x0020_10"></span></p>

</div>
