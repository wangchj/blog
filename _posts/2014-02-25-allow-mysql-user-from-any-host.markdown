---
layout: post
status: publish
published: true
title: Allow MySQL User From Any Host
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 618
wordpress_url: http://codenuggets.com/?p=618
date: '2014-02-25 00:56:53 -0600'
date_gmt: '2014-02-25 00:56:53 -0600'
categories:
- Research
- SQL/MySQL
tags:
- MySQL
- database
- MySQL 5.5
- user
- permission
- anonymous user
comments: []
---
Recently I have made a few new instances of MySQL server for my research. I have created a database and a user for the database, and I want to be able to access the database from any computer via that user. The following is the command I used.

{% highlight sql %}
create database Project;
create user 'proj_user' identified by 'password';
grant all on Project.* to 'proj_user';
{% endhighlight %}

The first line creates the database, the second line creates the user, and the third line says give all permission to 'proj_user' for the database 'Project'.

Now the <a href="http://dev.mysql.com/doc/refman/5.1/en/create-user.html">documentation</a> says when host name (or host IP) is omitted, any host, which is denoted by '**%**' is assumed for this user.

This is great and exactly what I need. But when I try to log in with my new user account, I get an error message.

```
mysql -u proj_user -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'proj_user'@'localhost' (using password: YES)
```

I'm sure I typed in the correct password, so what's the deal here? After much research, I found that this error is one of MySQL security thing and I still don't understand why they do it this way. Basically, I need to remove some **anonymous** users from the server. So I log in using root and do the following.

```
mysql> use mysql;
Database changed

mysql> select host, user from user;
+-----------+------------------+
| host      | user             |
+-----------+------------------+
| %         | proj_user        |
| 127.0.0.1 | root             |
| ::1       | root             |
| desk      |                  |
| desk      | root             |
| localhost |                  |
| localhost | debian-sys-maint |
| localhost | root             |
+-----------+------------------+
8 rows in set (0.00 sec)
```

From the output above, I found out that I have 2 anonymous users in the system (with blank user entry): one for host 'desk' and the other for 'localhost'.

I remove the anonymous for localhost with

{% highlight sql %}
drop user ''@'localhost';
{% endhighlight %}

And I was able to log in using my new user name.

---<br />
<a href="http://bugs.mysql.com/bug.php?id=31061">Bug #31061 Host wildcard % which is said in docs that means "all hosts" excludes localhost</a><br />
<a href="http://dev.mysql.com/doc/refman/5.5/en/privilege-system.html">http://dev.mysql.com/doc/refman/5.5/en/privilege-system.html</a><br />
<a href="https://dev.mysql.com/doc/refman/5.1/en/default-privileges.html">Securing the Initial MySQL Accounts</a>