---
layout: post
title: "How I Cracked a Hidden Flag Using Sublist3r and xxd"
date: 2025-07-17
categories: [osint, ctf, writeup]
tags: [sublist3r, xxd, hex, subdomain-enumeration, industrial-intrusion]
author: Michael Khanda
---

**Category**: OSINT  
**CTF**: Industrial Intrusion CTF  

## Challenge Overview

A reconnaissance task focused on the domain `virelia-water.it.com`. The goal: enumerate subdomains and uncover intelligence that reveals the flag.

## Step 1: Subdomain Enumeration with Sublist3r

```
sublist3r -d virelia-water.it.com
```

**Output:**

```
[-] Total Unique Subdomains Found: 2
54484d7b5375357373737d.virelia-water.it.com
stage0.virelia-water.it.com
```

The first subdomain immediately stands out — it looks like hex rather than a normal hostname.

## Step 2: Decode the Hex

Isolate the suspicious string and pipe it through `xxd`:

```bash
echo "54484d7b5375357373737d" | xxd -r -p
```

**Output:**

```
THM{Su5sss}
```

## Flag

```
THM{Su5sss}
```

## Key Takeaways

- Subdomain enumeration is one of the most effective passive recon techniques
- Hex-encoded strings in unexpected places (subdomains, DNS records) are worth investigating
- `xxd -r -p` is your quick decoder for hex strings in CTFs
