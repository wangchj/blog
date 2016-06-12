---
layout: post
status: publish
published: true
title: Installing Yii 2 Using Composer
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1053
wordpress_url: http://codenuggets.com/?p=1053
date: '2014-08-16 07:07:55 -0500'
date_gmt: '2014-08-16 07:07:55 -0500'
categories:
- Programming
- PHP
tags:
- Yii 2
- Comoser
comments:
- id: 3733
  author: Ernesto
  author_email: ernest.leyva@gmail.com
  author_url: ''
  date: '2014-10-15 02:14:03 -0500'
  date_gmt: '2014-10-15 02:14:03 -0500'
  content: "On Ubuntu 14.04 just need to do only three steps as sudo:\r\n\r\n#apt-get
    install php5-mcrypt\r\n#php5enmod mcrypt\r\n#service apache2 restart\r\n\r\nEnjoy..."
- id: 3796
  author: Jeff
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2014-10-22 19:30:58 -0500'
  date_gmt: '2014-10-22 19:30:58 -0500'
  content: I will give this a try. Thank you for the tip!
---
Today I decided to try to install and write a simple web app using the beta version of <a href="https://github.com/yiisoft/yii2" target="_blank">Yii Framework 2</a>. I have used Yii Framework 1.1 in a previous project and I liked it, so want to see what version 2 has to offer. My source of documentation is the official definitely guide, which is also in non-fished stage.

Apparently, version 2 of the framework is moving toward installation using Composer, which mimics Bundle from Ruby on Rails.

## Install PHP mcrypt

Yii 2 requires mcrypt and my system does not have it installed. The following steps install the module.

```
sudo apt-get install php5-mcrypt
sudo mv -i /etc/php5/conf.d/mcrypt.ini /etc/php5/mods-available/
sudo php5enmod mcrypt
sudo service apache2 restart
```

## Install Composer

The following command installs Composer in the `bin` directory in my home folder (local installation).

```
curl -sS https://getcomposer.org/installer | php -- --install-dir=bin
```

## Create Project

We can start creating our project using Composer, which will create a folder for our project and download dependencies including Yii.

As of writing, we can only install the dev version of Yii. The stable channel does not work. The following installs the development version, and create a project folder called `basic`

```
~/bin/composer create-project --prefer-dist --stability=dev yiisoft/yii2-app-basic basic
```