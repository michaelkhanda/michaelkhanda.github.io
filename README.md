# michaelkhanda.github.io

Personal portfolio. I store everything I'm learning here — CTF writeups, security research, and notes. Built with Jekyll, hosted on GitHub Pages.

## Adding a post

Create a file in `_posts/` named `YYYY-MM-DD-title.md`:

```markdown
---
layout: post
title: "Challenge Title"
date: YYYY-MM-DD
categories: [forensics, ctf]
tags: [wireshark, volatility]
author: Michael Khanda
---

Writeup content here.
```

Categories: `forensics` `web` `pwn` `osint` `crypto` `rev`

## Local dev

```bash
bundle exec jekyll serve --livereload
```

Live at [michaelkhanda.github.io](https://michaelkhanda.github.io)
