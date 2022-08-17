---
layout: post
title: THM - Cyborg Write Up
---

### Introduction

Cyborg was the first CTF that I completed on the popular website TryHackMe. It is for beginners like myself so that was perfect. I'll start with some enumeration.

<img src="https://i.postimg.cc/ZqdVsrgy/CYBORG1.png">

### Enumeration

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