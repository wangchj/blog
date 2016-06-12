---
layout: post
status: publish
published: true
title: Download File on Linux over SSH without Active Shell
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 6
wordpress_url: http://codenuggets.com/?p=6
date: '2012-02-14 04:25:15 -0600'
date_gmt: '2012-02-14 04:25:15 -0600'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
tags:
- Linux
- ssh
- wget
- screen
comments:
- id: 32
  author: Brigite
  author_email: cauemorto@hotmail.com
  author_url: http://www.shoppingpantanal.net
  date: '2012-03-26 10:07:47 -0500'
  date_gmt: '2012-03-26 10:07:47 -0500'
  content: i'm trying to understand more about this subject, can you explain it clearer?
- id: 34
  author: SuperNugget
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2012-03-26 17:15:23 -0500'
  date_gmt: '2012-03-26 17:15:23 -0500'
  content: Which part is unclear?
- id: 45
  author: Wesley Emond
  author_email: Cutcher41@gmail.com
  author_url: http://www.mhvmkrce.net
  date: '2012-04-04 18:21:19 -0500'
  date_gmt: '2012-04-04 18:21:19 -0500'
  content: Excellent post. I was checking constantly this blog and I'm inspired! Extremely
    helpful info specifically the final phase :) I deal with such info much. I used
    to be looking for this particular information for a very long time. Thank you
    and best of luck.
---
I'm trying to download a few pretty large dataset onto a Linux machine at school using SSH on my Mac from home. I'm using `wget` to get the files as follows:

```
wget dataset.zip
```

The problem is when I close my SSH client, the shell session on the Linux machie ends and killing my wget processes. I read online to use the `screen` command to keep my processes alive. The command follows:

```
screen wget dataset.zip
```

After entering the above command, then press `Ctrl+A+D` to detach the screen and go back to the original shell and the SSH session can be terminated.

