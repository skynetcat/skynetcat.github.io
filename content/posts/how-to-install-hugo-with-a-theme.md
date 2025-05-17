---
title: "How to Install Hugo With a Theme"
date: 2025-05-17T20:57:31Z
lastmod: 2025-05-17T20:57:31Z
draft: true
author: "Skynetcat"
authorLink: "https://skynetcat.github.io/about"

tags: []
categories: []

featuredImage: ""
featuredImagePreview: ""

hiddenFromHomePage: false
hiddenFromSearch: false
---
Having a blog is an important step in the Tech journey and I realized that too late.
<!--more-->
I spent years using Linux and open-source apps, solved a handful of problems and forgot how I did that later. This time I thankfully made the blog I have been procrastinating on for so long. 

Maybe this will help me remember what I did later on or be a ready-to-use guide in case I forget about how I solved my problems.

## 1. Find a Hugo theme
Wait ... what? Yea you saw that right.

Go find the theme first because Hugo is ever changing and sometimes theme developers can't keep up with the updates.

The [LoveIt theme](https://github.com/dillonzq/LoveIt) you see right now is an example of that. As of the time I'm writing this, Hugo released [v0.147.3](https://github.com/gohugoio/hugo/releases) and the last version this theme supports is [v0.145.0](https://github.com/dillonzq/LoveIt/issues/971).

You can find themes at [Hugo Theme Library](https://themes.gohugo.io/themes/).

## 2. Install a compatible version of Hugo
Once you've checked the themes and found a one you like, make sure to check the last version of Hugo it's compatible with. 

If it's the latest, you're good to go and you can install it through your **package-manager**.

If not, then you'd have to install using go. [Refer to the Hugo documentation](https://gohugo.io/installation/).

This is the command I used to install v0.145.0 :
```bash
go install github.com/gohugoio/hugo@v0.145.0
```

Make sure to include `$HOME/go/bin/` in your `$PATH` variable. I modified the it in my `~/.bashrc` accordingly by appending `:$HOME/go/bin/` to the end of `$PATH` :
```bash
export PATH="$PATH:$HOME/go/bin"
```
