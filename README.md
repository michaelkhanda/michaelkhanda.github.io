# michaelkhanda.github.io

Personal Portfolio. I store all information about what I am learning on this blog.

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
