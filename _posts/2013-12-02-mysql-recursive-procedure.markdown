---
layout: post
status: publish
published: true
title: MySQL Recursive Procedure
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 597
wordpress_url: http://codenuggets.com/?p=597
date: '2013-12-02 20:37:12 -0600'
date_gmt: '2013-12-02 20:37:12 -0600'
categories:
- Programming
- SQL/MySQL
tags:
- MySQL
- SQL
- stored procedure
- recursion
comments: []
---
I'm trying to write a recursive stored procedure or function to auto-generate large amount of hierarchical (tree) data for dissertation experiment.

What I find out is that, in MySQL, only recursive stored procedure is allowed, where stored function is not allowed. So, the following procedure works:

{% highlight sql %}
delimiter //
create procedure rec_seq(min int, max int, result text)
begin
	-- Put current value into result
	set result = concat(result, min);
	if min != max then
		set result = concat(result, ' ');
	end if;
	
	if min = max then
		-- Output result
		select result;
	else
		-- Recursive call
		call rec_seq(min + 1, max, result);
	end if;
end//
delimiter ;
{% endhighlight %}

Where as the following very similar stored function will not run:

{% highlight sql %}
delimiter //

create function rec_seq(min int, max int) RETURNS text CHARSET latin1
begin
	if min = max then
		return min;
	end if;

	set @result = '';
	set @result = concat(@result, min);
	set @result = concat(@result, ',');
	set @result = concat(@result, rec_seq(min + 1, max));
	return @result;
end//
{% endhighlight %}

To run the stored procedure, we need to increase the max_sp_recursion_depth, which is set to 0 on my installation. To run the procedure, I execute the following:

{% highlight sql %}
set max_sp_recursion_depth = 200;
call rec_seq(1,10, '');
{% endhighlight %}

This produce the following output:

```
mysql> call rec_seq(1,10,'');
+----------------------+
| result               |
+----------------------+
| 1 2 3 4 5 6 7 8 9 10 |
+----------------------+
1 row in set (0.00 sec)

Query OK, 0 rows affected (0.00 sec)
```

When I run the stored procedure with range from 1 to 15, even with this simple script I get a stack overflow error:

```
mysql> call rec_seq(1,12,'');
ERROR 1436 (HY000): Thread stack overrun:  70208 bytes used of a 196608 byte stack, and 128000 bytes needed.  Use 'mysqld --thread_stack=#' to specify a bigger stack.
```

My solution was to edit /etc/mysql/my.cnf and change thread_stack from 192k to a higher value. The following is my change:

```
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
**thread_stack            = 512K**
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
```

**References**

http://www.mysqltutorial.org/stored-procedures-parameters.aspx

http://stackoverflow.com/questions/3536538/mysql-does-not-support-recursive-functions-why-since-when

http://stackoverflow.com/questions/8821575/mysql-error-1436-thread-stack-overrun-with-simple-query