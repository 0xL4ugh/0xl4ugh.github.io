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

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>Okay first I download the file and it was pcap file so I opened
it and went through tcp streams till I found stream 4 include zip file header
and file name called = “da_op_files.zip”</span></p>

<p class=MsoNormal align=center style='text-align:center'><img border=0 width=624 height=339 id="Picture 1" src="/assets/img/Reprisal_files/image001.jpg"></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady"'>So I extracted
this file by using network miner</span></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady"'><br>
<br>
<br>
<br>
</span><span style='position:relative;z-index:251658240'><span
style='left:0px;position:absolute;left:400px;top:-48px;width:624px;height:415px'><img width=624 height=415 src="/assets/img/Reprisal_files/image002.jpg"></span></span><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady"'><br>
<br>
</span></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='font-size:18.0pt;line-height:107%;font-family:"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='mso-no-proof:yes'><img border=0 width=624 height=388 id="_x0000_i1031"
src="/assets/img/Reprisal_files/image003.jpg"></span><span style='font-size:18.0pt;
line-height:106%;font-family:"Abd ElRady"'><o:p></o:p></span></p>

<p class=MsoNormal align=center style='text-align:center'><o:p>&nbsp;</o:p></p>

<p class=MsoNormal align=center style='text-align:center'><span
style='font-size:18.0pt;line-height:106%;font-family:"Abd ElRady"'>So I
extracted data and I got 1 pdf and 1 <span class=SpellE>pcap</span> file so I
checked the <span class=SpellE>pcap</span> file but nothing interesting in it
so I tried if there is any tool to crack pdf password</span><span
style='mso-no-proof:yes'><img border=0 width=624 height=439 id="_x0000_i1030"
src="writeup_files/image004.jpg"></span><span style='font-size:18.0pt;
line-height:106%;font-family:"Abd ElRady"'><o:p></o:p></span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>So I extracted data and I got 1 pdf and 1 pcap file so I checked the
pcap file but nothing interesting in it so I tried if there is any tool to
crack pdf password</span><img border=0 width=624 height=439 id="Picture 4" src="/assets/img/Reprisal_files/image004.jpg"><span style='font-size:18.0pt;line-height:
107%;font-family:"Abd ElRady"'> so I found that there is pdf2john.pl</span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>So I tried it and I got the password = “ ihatehackers ” </span></p>

<p class=MsoNormal><img border=0 width=624 height=120 id="Picture 5" src="/assets/img/Reprisal_files/image005.jpg"></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>So it’s looks like base64</span></p>

<p class=MsoNormal><img border=0 width=624 height=303 id="Picture 6" src="/assets/img/Reprisal_files/image006.jpg"></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>So I can see that it’s png from the header and footer </span></p>

<p class=MsoNormal><img border=0 width=624 height=320 id="Picture 7" src="/assets/img/Reprisal_files/image007.jpg"></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>So after I used it wow it’s corrupted !!!</span></p>

<p class=MsoNormal><img border=0 width=624 height=326 id="Picture 8" src="/assets/img/Reprisal_files/image008.jpg"></p>

<p class=MsoNormal><span style='font-size:18.0pt;line-height:107%;font-family:
"Abd ElRady"'>So I started to fix it and boom the flag:<br>
</span><img border=0 width=625 height=157 id="Picture 9" src="/assets/img/Reprisal_files/image009.jpg"></p>

</div>
