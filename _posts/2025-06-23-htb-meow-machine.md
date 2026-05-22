---
layout: post
title: "Box 1 of My Return to HTB — One Year Later"
date: 2025-06-23
categories: [ctf, writeup]
tags: [hackthebox, telnet, enumeration, starting-point]
author: Michael Khanda
---

**Machine**: Meow  
**Platform**: Hack The Box — Starting Point  
**Difficulty**: Very Easy  
**OS**: Linux

## Background

Returning to Hack The Box after a year away to join fr334aks-Mini — a team that requires members to solve CTF challenges and document their process. This is box one.

## Step 1: Enumeration

```bash
sudo nmap -sV {target_ip}
```

Telnet is running on **port 23** — an old protocol used for command-line remote access, rarely seen in production anymore but common in beginner HTB boxes.

## Step 2: Connect via Telnet

```bash
telnet {target_ip}
```

Misconfigured services sometimes leave default accounts with blank passwords. Common usernames to try: `admin`, `administrator`, `root`.

Trying `root` with no password grants immediate access.

## Step 3: Get the Flag

```bash
ls
cat flag.txt
```

## Flag

```
{flag from machine}
```

## Key Takeaways

- Telnet sends everything in plaintext — never use it on production systems
- Default/blank credentials are still a real attack vector
- Banner grabbing during enumeration can reveal service versions and misconfigurations
- Starting Point boxes are great for building muscle memory on the basics before moving to harder machines
