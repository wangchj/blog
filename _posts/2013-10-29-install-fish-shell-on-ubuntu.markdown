---
layout: post
status: publish
published: true
title: Install Fish Shell on Ubuntu
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 580
wordpress_url: http://codenuggets.com/?p=580
date: '2013-10-29 22:06:28 -0500'
date_gmt: '2013-10-29 22:06:28 -0500'
categories:
- Uncategorized
tags:
- Linux
- Ubuntu
- shell
- fish shell 2
- software package
comments: []
---
Fish shell is a modern command shell that offers great features. One of my favorite is that fish will parse man pages and provide command hints as you type a command. More about fish shell can be found at <a href="http://fishshell.com/">http://fishshell.com/</a>.

Fish shell can be easily install on Ubuntu with the following commands.

```
sudo apt-add-repository ppa:fish-shell/release-2
sudo apt-get update
sudo apt-get install fish
```

This command makes fish the default shell.

```
chsh -s /usr/bin/fish
```