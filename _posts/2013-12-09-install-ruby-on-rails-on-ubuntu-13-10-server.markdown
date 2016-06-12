---
layout: post
status: publish
published: true
title: Install Ruby on Rails on Ubuntu 13.10 Server
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 610
wordpress_url: http://codenuggets.com/?p=610
date: '2013-12-09 20:33:26 -0600'
date_gmt: '2013-12-09 20:33:26 -0600'
categories:
- Programming
- Ruby on Rails
tags:
- Linux
- Ubuntu
- Ubuntu 13.10
- Ubuntu 13.10 Server
comments: []
---
Note the following is done is Bash shell.

```
# Install Curl
sudo apt-get -y install curl

# Install RVM, Ruby, and Rails at once. This will take about 40 mins
\curl -sSL https://get.rvm.io | bash -s stable --rails

# Install Node.js
sudo apt-get -y install nodejs
```