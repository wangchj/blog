---
layout: post
status: publish
published: true
title: Ubuntu Software Bundle Python Script
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 588
wordpress_url: http://codenuggets.com/?p=588
date: '2013-11-06 23:10:04 -0600'
date_gmt: '2013-11-06 23:10:04 -0600'
categories:
- Uncategorized
tags:
- Linux
- Ubuntu
- Python
- software package
- Ubuntu 13.10
comments: []
---
The following script installs the software packages I use in Ubuntu 13.10.

ubu-install.py

{% highlight python %}
#!/usr/bin/env python

import subprocess

repos = [
    'ppa:fish-shell/release-2',
    'ppa:git-core/ppa'
]

packages = [
    'openjdk-7-jre',    #Java JRE
    'openjdk-7-jdk',    #Java JDK
    'icedtea-7-plugin', #Java browswer plugin
    'fish',
    'ssh',
    'sshfs',
    'apache2',
    'php5',
    'php5-dev',
    'php5-curl',
    'php5-json',
    'php-pear',
    'libapache2-mod-php5',
    'php5-mysql',
    #'mysql-server',
    'mysql-client',
    'git',
    'google-chome-stable',
    'vim'
    #sublime text,
    #'mono-runtime',
    #'mono-gmcs',
    #'libapache2-mod-mono',
    #'mono-apache-server2',
    'gedit-plugins'
]

def exe(command):
    return subprocess.call(command, shell=True)


#Configure MySQL non-interactive configuration.
#exe('sudo debconf-set-selections <<< 
mysql-server-5.5 mysql-server/root_password password $ud0random
')
#exe('sudo debconf-set-selections <<< 
mysql-server-5.5 mysql-server/root_password_again password $ud0random
')

#Configure Google Chrome
exe('wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -')
exe('sudo sh -c 
echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list
')
    
for repo in repos:
    exe('sudo apt-add-repository -y ' + repo)

exe('sudo apt-get -y update')


for package in packages:
    exe('sudo apt-get -y install ' + package)

#Set fish as the default shell
exe('chsh -s /usr/bin/fish')

#Post-installation configuration for Apache 2
exe('mkdir ~/public_html')
exe('sudo ln -s /etc/apache2/mods-available/userdir.load /etc/apache2/mods-enabled/')
exe('sudo ln -s /etc/apache2/mods-available/userdir.conf /etc/apache2/mods-enabled/')
exe('sudo /etc/init.d/apache2 restart')

#Post-installation configuration for MySQL
#exe('sudo mysql_secure_installation')

#Install Xdebug
exe('sudo pecl install xdebug')

#Install PHPUnit
#exe('sudo pear config-set auto_discover 1')
#exe('sudo pear install pear.phpunit.de/PHPUnit')
#exe('sudo pear install --alldeps --force phpunit/phpunit')
#exe('sudo pear install phpunit/DbUnit')
#exe('sudo pear install phpunit/PHPUnit_Story')
#exe('sudo pear install phpunit/PHPUnit_Selenium')

print 'Reminder: edit /etc/mysql/my.cnf to allow MySQL remote access.'
print 'Reminder: edit /etc/apache2/modes-enabled/php5.conf to allow PHP in user directory.'
print 'Reminder: configure /etc/php5/apache2/php.ini to enable xdebug.'
{% endhighlight %}