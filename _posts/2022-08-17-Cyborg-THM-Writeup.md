---
layout: post
title: THM - Cyborg Write Up
---

### Introduction

Cyborg was the first CTF that I completed on the popular website TryHackMe. It is for beginners like myself so that was perfect. I'll start with some enumeration.

<img src="https://i.postimg.cc/ZqdVsrgy/CYBORG1.png">

### Enumeration

I have decided to run an nmap scan on the IP address provided to see can the first couple of questions be answered.

{% highlight text %}
root@ip-10-10-145-36:~# nmap -sC -sV -T4 -p- -Pn -vv 10.10.28.93

Starting Nmap 7.60 ( https://nmap.org ) at 2022-08-17 19:13 BST
NSE: Loaded 146 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 19:13
Completed NSE at 19:13, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 19:13
Completed NSE at 19:13, 0.00s elapsed
Initiating ARP Ping Scan at 19:13
Scanning 10.10.28.93 [1 port]
Completed ARP Ping Scan at 19:13, 0.22s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 19:13
Completed Parallel DNS resolution of 1 host. at 19:13, 0.00s elapsed
Initiating SYN Stealth Scan at 19:13
Scanning ip-10-10-28-93.eu-west-1.compute.internal (10.10.28.93) [65535 ports]
Discovered open port 22/tcp on 10.10.28.93
Discovered open port 80/tcp on 10.10.28.93
{% endhighlight %}

As you can see above there is two open ports 22/ssh & 80/http. 

Next I decide to run a web content sanner to see what directories are available to navigate to. I have used dirb for this. It is pretty easy to use as can be seen below.

{% highlight text %}
root@ip-10-10-145-36:~# dirb http://10.10.28.93

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Wed Aug 17 19:23:38 2022
URL_BASE: http://10.10.28.93/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://10.10.28.93/ ----
==> DIRECTORY: http://10.10.28.93/admin/                                                                                                                                                                          
==> DIRECTORY: http://10.10.28.93/etc/                                                                                                                                                                            
+ http://10.10.28.93/index.html (CODE:200|SIZE:11321)                                                                                                                                                             
+ http://10.10.28.93/server-status (CODE:403|SIZE:276)                                                                                                                                                            
                                                                                                                                                                                                                  
---- Entering directory: http://10.10.28.93/admin/ ----
+ http://10.10.28.93/admin/index.html (CODE:200|SIZE:5771)                                                                                                                                                        
                                                                                                                                                                                                                  
---- Entering directory: http://10.10.28.93/etc/ ----
(!) WARNING: Directory IS LISTABLE. No need to scan it.                        
    (Use mode '-w' if you want to scan it anyway)
                                                                               
-----------------
END_TIME: Wed Aug 17 19:23:44 2022
DOWNLOADED: 9224 - FOUND: 3
{% endhighlight %}

