---
layout: post
status: publish
published: true
title: Git Ignore File Only in Current Directory
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1019
wordpress_url: http://codenuggets.com/?p=1019
date: '2014-08-07 04:15:17 -0500'
date_gmt: '2014-08-07 04:15:17 -0500'
categories:
- Version Control
- Git
tags: []
comments:
- id: 4380
  author: Jesus
  author_email: nolabadillo@freenet.de
  author_url: http://Rachele.tv
  date: '2015-03-21 03:45:50 -0500'
  date_gmt: '2015-03-21 03:45:50 -0500'
  content: "You can earn some extra $$$ from your blog, i see couple opportunities
    here.\r\nYou should search in google for:\r\nYoogurn's money making"
---
I have a paper written in LaTex and I use `pdflatex` to compile the paper directly to a PDF file. In addition, I have figures also in PDF format stored in a sub-folder of the main project. I don't want Git to version my output PDF file, but I do want my PDF figures to be tracked.

In other words, I want to ignore all PDF files in my main project folder, but not PDF files in sub-folders.

I found that this is very simple and all I have to do is, in my `.gitignore` file, add a forward slash to the file type I want to ignore, but not in sub-directories. The `.gitignore` file is what I use in my project. Notice the forward slash in front of `*.pdf`

```
*.bak
*.log
*.sav
*.aux
*.bbl
*.blg
*.dvi
/*.pdf
._*
*.synctex.gz
```