---
layout: post
status: publish
published: true
title: Install Git on Ubuntu
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 453
wordpress_url: http://codenuggets.com/?p=453
date: '2013-04-09 20:26:04 -0500'
date_gmt: '2013-04-09 20:26:04 -0500'
categories:
- Version Control
- Git
tags:
- Linux
- Ubuntu
- Ubuntu 10.04
comments: []
---
**1. Add PPA repository**<br />
Official Ubuntu software repository usually do not have the latest version of software packages (in this case git). Personal Package Archives (PPA) are maintained by the developer of a specific software, therefore usually have the latest version. To get the latest version of git, add PPA for git to software sources as follows:

```
sudo add-apt-repository ppa:git-core/ppa
```
**2. Update and Install**<br />
Then git can be installed or updated.

```
sudo apt-get update
sudo apt-get install git
```

**References**<br />
http://adammonsen.com/post/665<br />
https://help.launchpad.net/Packaging/PPA