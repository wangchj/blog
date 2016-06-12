---
layout: post
status: publish
published: true
title: SQLite 3 Management Software for Mac OS X
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 245
wordpress_url: http://codenuggets.com/?p=245
date: '2012-05-20 20:12:59 -0500'
date_gmt: '2012-05-20 20:12:59 -0500'
categories:
- Programming
- Projects
- Dislike
tags:
- Yii
- data-driven webite
- Mac OS X
comments:
- id: 2147
  author: jorje
  author_email: sabojorjes@hotmail.com
  author_url: ''
  date: '2013-06-26 05:29:58 -0500'
  date_gmt: '2013-06-26 05:29:58 -0500'
  content: "I like use Valentina Studio on MAC OS X  http://www.valentina-db.com/en/valentina-studio-overview\r\n
    You can install Valentina Studio (FREE) directly from Mac App Store:  https://itunes.apple.com/us/app/valentina-studio/id604825918?ls=1&mt=12\r\nI
    very recommend check it."
- id: 2150
  author: SuperNugget
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2013-06-27 01:42:10 -0500'
  date_gmt: '2013-06-27 01:42:10 -0500'
  content: Thanks!
---
Due to its simplicity of design, I've decided to use SQLite on one of my web application project. The simplicity of SQLite means I can easily create multiple version of a database, such as a version for unit testing purposes, and when I need to move my database, all I have to do is copy the database file, since SQLite database is only ONE file.

I intend to write my web application on Mac OS X (using Yii Framework) therefore, I'm looking for a SQLite database management software, with which I can create/modify database, tables, and inspect data. One program that looks promising is the SQLite Administrator. Unfortunately it is for Windows, therefore I did not give it a try. These are the programs I tried:

- MesaSQLite
- Lita
- sqlite3: official SQLite client, which surprisingly came with Mac OS X (I run 10.6.8).

For now I settled with sqlite3 since I find it most flexible and intuitive. For the other two, I find the UI for Lita is more intuitive than MesaSQLite. Also I'm able to open database created with sqlite3 using Lita, but unable to do so with MesaSQLite.

