---
layout: post
status: publish
published: true
title: Install Django Framwork on Ubuntu using Pip
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 521
wordpress_url: http://codenuggets.com/?p=521
date: '2013-05-21 20:16:18 -0500'
date_gmt: '2013-05-21 20:16:18 -0500'
categories:
- Programming
- Python
- Django
tags:
- Linux
- Ubuntu
- Ubuntu 13.04
- pip
- Python
- Django
- Django 1.5.1
- installation
comments: []
---
Installing Django on Ubuntu 13.04 using pip. This version of Django requires Python 2.6.5 or higher <sup><a href="https://www.djangoproject.com/download/">1</a></sup>.

1. Install pip:

```
sudo apt-get install python-pip
```

2. Remove older version of Django.

According to the installation documentation, if the older version was installed using pip, then this step can be skipped, since pip will take care of updating to new version.

3. Install using pip

```
sudo pip install Django==1.5.1
```

At the end of installation, you should get the message 

```
Successfully installed Django
Cleaning up...
```

4. Verification

```
>>> import django
>>> print(django.get_version())
1.5.1
```