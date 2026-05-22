# Michael Khanda's CTF Blog

A Jekyll-based blog for CTF writeups, security research, and cybersecurity content. Built for free hosting on GitHub Pages with no paywalls.

## 🚀 Quick Start

### Prerequisites
- Git installed on your system
- Ruby (for local testing, optional)

### Setup Instructions

1. **Delete your old repository content** (backup first if needed):
```bash
cd ~/michaelkhanda.github.io
git rm -rf .
git commit -m "Clean slate for CTF blog"
```

2. **Copy the new blog structure**:
```bash
# Copy all files from this ctf-blog directory to your repo
cp -r /path/to/ctf-blog/* ~/michaelkhanda.github.io/
```

3. **Push to GitHub**:
```bash
cd ~/michaelkhanda.github.io
git add .
git commit -m "New Jekyll CTF blog setup"
git push origin main
```

4. **Enable GitHub Pages**:
   - Go to your repo settings on GitHub
   - Navigate to "Pages" section
   - Source: Deploy from branch `main` (or `master`)
   - Your site will be live at `https://michaelkhanda.github.io`

## 📝 Writing Blog Posts

### Post Format

Create new posts in the `_posts/` directory with this naming convention:
```
YYYY-MM-DD-title-of-post.md
```

### Post Template

```markdown
---
layout: post
title: "Your CTF Challenge Title"
date: YYYY-MM-DD
categories: [forensics, web, pwn, crypto, osint]
tags: [specific-tools, techniques, ctf-name]
author: Michael Khanda
---

**Category**: [Forensics/Web/Pwn/etc]  
**CTF**: [CTF Name and Date]  
**Difficulty**: [Easy/Medium/Hard]

## Challenge Overview

Brief description of the challenge...

## Solution

Your writeup here...

## Flag

```
FLAG{your_flag_here}
```

## Key Takeaways

- Learning point 1
- Learning point 2

## Tools Used

- Tool 1
- Tool 2
```

## 🔄 Migrating from Medium

### Option 1: Manual Conversion (Recommended for CTF posts)

1. Copy your Medium article content
2. Create a new `.md` file in `_posts/`
3. Add the frontmatter (the `---` section at top)
4. Paste and format your content in Markdown

### Option 2: Medium Export

1. Go to Medium Settings → Download your information
2. Extract the ZIP file
3. Convert HTML posts to Markdown using tools like:
   - [medium-to-markdown](https://www.npmjs.com/package/medium-to-markdown)
   - [Pandoc](https://pandoc.org/)

```bash
# Using pandoc
pandoc -f html -t markdown input.html -o output.md
```

## 🎨 Customization

### Update Site Info

Edit `_config.yml`:
```yaml
title: Your Name
description: Your description
email: your-email@example.com
github_username: yourusername
```

### Add Images

1. Place images in `assets/images/`
2. Reference in posts:
```markdown
![Alt text](/assets/images/your-image.png)
```

### Change Theme

The default theme is `minima`. To use other themes:

1. Browse themes at [Jekyll Themes](https://jekyllthemes.io/)
2. Update `_config.yml`:
```yaml
theme: theme-name
```

## 🧪 Local Testing (Optional)

To preview your blog locally before pushing:

```bash
# Install Jekyll
gem install bundler jekyll

# Install dependencies
bundle install

# Run local server
bundle exec jekyll serve

# Visit http://localhost:4000
```

## 📁 Directory Structure

```
michaelkhanda.github.io/
├── _config.yml          # Site configuration
├── _posts/              # Your blog posts
│   └── YYYY-MM-DD-title.md
├── assets/
│   └── images/          # Post images
├── about.md             # About page
├── index.md             # Homepage
├── Gemfile              # Ruby dependencies
└── README.md            # This file
```

## ✍️ Markdown Syntax Quick Reference

```markdown
# Heading 1
## Heading 2
### Heading 3

**bold text**
*italic text*
`inline code`

```bash
# Code block with syntax highlighting
echo "Hello World"
```

- Bullet point 1
- Bullet point 2

1. Numbered item 1
2. Numbered item 2

[Link text](https://example.com)
![Image alt text](/path/to/image.png)
```

## 🔧 Troubleshooting

### Site not updating?
- Wait 2-3 minutes after pushing
- Check GitHub Actions tab for build errors
- Ensure `_config.yml` has correct `url` and `baseurl`

### Posts not showing?
- Verify filename format: `YYYY-MM-DD-title.md`
- Check frontmatter formatting (correct YAML syntax)
- Ensure date is not in the future

### Build failing?
- Check for YAML syntax errors in `_config.yml`
- Verify all plugins are compatible with GitHub Pages
- Review GitHub Actions build logs

## 📚 Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)
- [Kramdown Syntax](https://kramdown.gettalong.org/syntax.html)

## 📞 Support

Questions? Issues? Reach out:
- Email: michaelkhanda006@gmail.com
- GitHub Issues: Open an issue on this repo

---

**Built with Jekyll • Hosted on GitHub Pages • Free Forever • No Paywalls**
