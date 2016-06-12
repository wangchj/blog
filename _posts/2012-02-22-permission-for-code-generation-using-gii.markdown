---
layout: post
status: publish
published: true
title: Permission for code generation using Gii
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 31
wordpress_url: http://codenuggets.com/?p=31
date: '2012-02-22 02:54:14 -0600'
date_gmt: '2012-02-22 02:54:14 -0600'
categories:
- Programming
- PHP
- Projects
- Dislike
tags:
- PHP
- Yii
comments:
- id: 667
  author: Alex
  author_email: alex@peskydonut.com
  author_url: ''
  date: '2012-05-24 16:57:46 -0500'
  date_gmt: '2012-05-24 16:57:46 -0500'
  content: You can also do chown 775 and chgrp [name-of-your-webserver-group]. Slightly
    less insecure ;-)
- id: 668
  author: SuperNugget
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2012-05-24 18:26:26 -0500'
  date_gmt: '2012-05-24 18:26:26 -0500'
  content: Alex, yes you're right, but I haven't yet found the user and group under
    which my Apache web server is running on Mac OS X.
- id: 674
  author: Alex
  author_email: alex@peskydonut.com
  author_url: ''
  date: '2012-06-06 21:37:12 -0500'
  date_gmt: '2012-06-06 21:37:12 -0500'
  content: I believe it's '_www'
---
I'm setting up my Dislikes application and using Yii's Gii to generate my models and controllers, but I'm getting the following errors:

```
generating controllers/UserController.php
    Unable to write the file '[Application Path]/protected/controllers/UserController.php'.
generating views/user/index.php
    Unable to create the directory '[Application Path]/protected/views/user'.
```

To solve this, I need to set the permission of the following directories to 777 on my dev machine, and change the permission to more restrictive when I upload the project to the production server


- models
- controllers
- views