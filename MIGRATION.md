# Medium to Jekyll Migration Guide

This document outlines how to migrate your existing Medium posts to your new Jekyll blog.

## Your Medium Posts to Migrate

Based on your Medium profile, here are your posts:

1. **Deobfuscating a PowerShell Reverse Shell from PCAP** (Sep 5, 2025) - Forensics
2. **Exploiting a Time-of-Check to Time-of-Use (TOCTOU) Bug** (Aug 6, 2025) - Web
3. **How I Cracked a Hidden Flag Using Sublist3r and xxd** (Jul 17, 2025) - OSINT
4. **Try Hack Me Industrial Intrusion CTF: Buffer Overflow** (Jun 30, 2025) - Pwn
5. **Box 1 of My Return to HTB—One year Later** (Jun 23, 2025) - General
6. **Client Authentication and Remote Access in PostgreSQL** (Feb 20, 2024) - Dev
7. **Three Months In: My Soccer Data Analyst Internship** (Jan 19, 2024) - Personal
8. **A Beginner's Guide to Moving Projects to GitHub** (Aug 23, 2023) - Dev

## Migration Process

### Step 1: Export from Medium

1. Go to https://medium.com/me/settings
2. Click "Download your information"
3. Wait for the email with download link
4. Extract the ZIP file

### Step 2: Manual Conversion (Recommended for CTF posts)

For each CTF writeup:

1. Open your Medium post
2. Copy the content
3. Create new file: `_posts/YYYY-MM-DD-title.md`
4. Add frontmatter:

```markdown
---
layout: post
title: "Exact Title from Medium"
date: 2025-09-05
categories: [forensics, ctf]
tags: [wireshark, powershell, world-wide-flags]
---
```

5. Paste content below frontmatter
6. Format as Markdown (see examples below)

### Markdown Conversion Examples

#### Medium Format:
```
Bold Text: This is important
Code: `command here`
Code Block: (Medium auto-detects)
```

#### Jekyll Markdown:
```markdown
**Bold Text**: This is important
Code: `command here`
Code Block:
```bash
command here
```
```

## Quick Start Files

I've already created one sample post for you:
- `_posts/2025-09-05-deobfuscating-powershell-reverse-shell.md`

Use this as a template for your other writeups.

## Recommended Post Categories

Based on your content:

**CTF Writeups:**
- `[forensics, ctf, writeup]` - For forensics challenges
- `[web, ctf, writeup]` - For web exploitation
- `[pwn, binary, ctf]` - For binary exploitation
- `[osint, recon, ctf]` - For OSINT challenges

**Dev Posts:**
- `[development, tutorial]` - For technical guides
- `[postgresql, database]` - For database posts
- `[career, internship]` - For career-related content

## Tags to Use

Common tags for your posts:
- CTF names: `world-wide-flags`, `hackthebox`, `tryhackme`
- Tools: `wireshark`, `burpsuite`, `ghidra`, `sublist3r`
- Techniques: `buffer-overflow`, `sql-injection`, `pcap-analysis`
- Languages: `powershell`, `python`, `bash`

## Image Migration

1. Download images from your Medium posts
2. Save to `assets/images/`
3. Reference in posts:

```markdown
![Description](/assets/images/filename.png)
```

## Priority Migration Order

I recommend migrating in this order:

1. ✅ **PowerShell PCAP** (Done - sample created)
2. **TOCTOU Bug** - Web writeup
3. **Industrial Intrusion** - Buffer overflow
4. **Sublist3r Flag** - OSINT
5. **HTB Return** - General pentesting
6. Dev posts (optional - if you want to keep them)

## Automated Tools (Alternative)

If you want to automate the conversion:

```bash
# Install medium-to-markdown
npm install -g medium-to-markdown

# Convert a post
medium-to-markdown https://medium.com/@michaelkhanda/your-post-url > output.md
```

Then clean up the output and add proper frontmatter.

## Checklist for Each Post

- [ ] Created file with correct date format
- [ ] Added complete frontmatter
- [ ] Converted to proper Markdown
- [ ] Added images to assets/images/
- [ ] Updated image paths
- [ ] Tested code blocks with syntax highlighting
- [ ] Verified flag format
- [ ] Added relevant tags and categories
- [ ] Proofread for formatting issues

## Final Notes

- **Don't rush**: Take time to format each post properly
- **Test locally**: Use `bundle exec jekyll serve` to preview
- **Keep it clean**: Remove Medium-specific elements (claps, reading time, etc.)
- **Add value**: Consider adding "Update" sections with new insights

---

Need help? Check the main README.md or reach out!
