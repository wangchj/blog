---
layout: post
status: publish
published: true
title: Likewise Open Change Default User Shell
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 723
wordpress_url: http://codenuggets.com/?p=723
date: '2014-05-15 21:17:47 -0500'
date_gmt: '2014-05-15 21:17:47 -0500'
categories:
- School
- OS
- Ubuntu
tags:
- Ubuntu 14.04
- Likewise-Open
comments: []
---
In the past week, I've been configuring a Ubuntu 14.04 computer to allow user to log in using their credentials stored in a Active Directory server on our network.

The machine was configured with Likewise-Open package. After the system is configured, I realized when a user logs in using `ssh`, the default shell is `/bin/sh` and I'd really like to change that to fish shell `/usr/bin/fish`. The following command does exactly that.

```
sudo /opt/likewise/bin/lwregshell set_value '[HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory]' LoginShellTemplate /usr/bin/fish
sudo /opt/likewise/bin/lwregshell set_value '[HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\Local]' LoginShellTemplate /usr/bin/fish
```

Then refresh Local Security Service:

```
sudo /opt/likewise/bin/lwsm refresh lsass
```

Now you also need to clear LikeWise's Active Directory Cache if users have already logged in and you want it to take effect immediately:  (if this is done during setup you can skip this step)

```
sudo /opt/likewise/bin/lw-ad-cache --delete-all
```

Reference:<br />
<a href="http://michael.requeny.com/2011/02/11/likewise-open-change-default-shell/" target="_blank">LikeWise Open: Change Default Shell</a>
