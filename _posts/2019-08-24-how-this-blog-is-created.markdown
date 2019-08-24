---
layout: post
title:  "How this blog is delivered"
date:   2019-08-22 01:08:44 +0200
categories: blog tech
---

### How this blog is delivered ###

This blog is hosted and delivered via github pages. You write blog content in Markdown and then use normal git workflow to push the blog
entries to Github. Github then builds and publishes the content as web pages.

Github pages can use either static html pages or can use Markdown and Jekyll which is a static page generator. Jekyll renders html pages 
from Markdown files. 

Steps to create Github personal pages
1. Create a git github.io repository
   
   Create a git repository named after your username.github.io
in my case `cnygaard.github.io`
2. Clone the newly created repository

   `git clone `
2. Create an index.md file in the top level of the git repository you just created
   add the index.md file to git with 
   
   `git add index.md`
3. Commit the index.md to github

   `git commit -am "Commit message"`
4. Push the updated content to Github

   `git push`
   
Now you have published your personal page to git. It takes a while for github to build your page up to ten minutes.
After its finished you will be able to visit your page at https://username.github.io in my case https://cnygaard.github.io


