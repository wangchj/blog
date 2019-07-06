---
layout: post
status: publish
published: true
title: ASP.NET Data-Bound Controls
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 37
wordpress_url: http://codenuggets.com/?p=37
date: '2012-02-26 04:57:22 -0600'
date_gmt: '2012-02-26 04:57:22 -0600'
categories:
- Programming
- Projects
- Auburn Interconnect
- ASP.NET
- ".NET"
- C#
tags:
- ASP.NET
- data-driven webite
- server controls
- data-bound control
comments:
- id: 33
  author: Edvaldo
  author_email: carlasantos650@hotmail.com
  author_url: http://www.bobesponjajogos.org
  date: '2012-03-26 10:34:24 -0500'
  date_gmt: '2012-03-26 10:34:24 -0500'
  content: exactly, i also got this post informative. really a good source i found.
    thanks.
- id: 52
  author: Eddy Tattersall
  author_email: Femia2779@gmail.com
  author_url: http://www.xvrjavnv.org
  date: '2012-04-05 02:51:54 -0500'
  date_gmt: '2012-04-05 02:51:54 -0500'
  content: I went over this website and I conceive you have a lot of good info, saved
    to fav (:.
- id: 77
  author: Sharilyn Preisner
  author_email: 35Coffie@yahoo.com
  author_url: http://www.site-publishing.com/story.php?id=370495
  date: '2012-04-07 21:37:28 -0500'
  date_gmt: '2012-04-07 21:37:28 -0500'
  content: I was  reading through  some of your  articles  on this website  and I  believe  this  site
    is  rattling informative !  Keep on  putting up.
- id: 86
  author: Lashawnda Amen
  author_email: Reynolds48338@yahoo.com
  author_url: http://indiahottrends.com/
  date: '2012-04-08 00:37:59 -0500'
  date_gmt: '2012-04-08 00:37:59 -0500'
  content: Hello, just wanted to say, I liked this blog post. It was practical. Keep
    on posting!
---
**Introduction**

I've been working on the Auburn InterConnect project recently. This is the first post about this project so I put a tad bit introduction about the project. Auburn InterConnect is an event management website designed for Auburn University Graduate School, mostly for international students. The goal is to make connection between local and international students by creating and organizing events to help students with culture here in Auburn.

As of now, the website is written in ASP.NET with C# and .NET Framework. The website is built using .NET Framework 4, but does not utilizes any feature of C# pass 2.0. The data store is SQLServer 2008 R2.

**Old Way of Doing Things**

Now the technical part. As with any data-driven website, Auburn InterConnect stores and populates the website with events stored in the database. At the beginning of the project, I did not know about ASP.NET data-bound controls. I had to write SQL statement and perform queries manually using  SQLConnection and SQLCommand objects to retrieve records into some kind of iterator, such as SqlDataReader, and write custom presentation code (HTML) to display individually.  While this give you total control, it is very <em>time consuming</em> to get all parts (especially the presentation layer) just right. The following is a gist of what I have to do.

{% highlight c# %}
//Write SQL statement
string queryStr = "SELECT eventId, eventName, startTime FROM [Events] " +
    "WHERE creatorId=@cid AND approved=1 AND endTime>@now " +
    "ORDER BY [Events].startTime";

//Create connection and query parameters
SqlConnection con = new SqlConnection(Config.SqlConStr);
SqlCommand command = new SqlCommand(queryStr, con);
command.Parameters.Add(new SqlParameter("cid", userId));
command.Parameters.Add(new SqlParameter("now", DateTime.Now));
con.Open();

//Execute query
SqlDataReader reader = command.ExecuteReader();

//Create HTML table and for each record, create table row, etc..
{% endhighlight %}

**Using Data-Bound Controls**

I had always known about the GridView server control in ASP.NET even when I was doing things manually (as above) but never took a good look at it. It turns out GridView is just one of many controls in ASP.NET called <a href="http://msdn.microsoft.com/en-us/library/ms228214.aspx">data-bound controls</a> designed to make creating data-driven websites easier.

To use a data-bound control, just drag a control (e.g. GridView) onto the design canvas, and click on the smart tag of the control to connect the control to a data source as shown in figure below. In Choose Data Source, select New Data Source, and select your database connection. This will add a new DataSource object to your page.

<a href="/images/uploads/2012/02/gridview_smarttag.png"><img class="size-medium wp-image-45 " title="GridView Smart Tag" src="/images/uploads/2012/02/gridview_smarttag-300x109.png" alt="GridView Smart Tag" width="300" height="109" /></a> GridView Smart Tag

During the configuration of the data source, you can still manually write your SQL statements, but the tool also include a Query Builder, which can be used to visually build the query as shown below.

<a href="/images/uploads/2012/02/querybuilder.png"><img src="/images/uploads/2012/02/querybuilder-300x218.png" alt="" title="Query Builder" width="300" height="218" class="size-medium wp-image-47" /></a> Visual Studio Query Builder

After finish configuration the data source, we have a grid with data from our database on the page.

One obvious benefits is that we do not need to manually create table and write HTML code to display our data. Another benefit is that we no longer have to manually execute the SQL commands in our code. The data-bound control will execute the queries when it binds and render the data.

We can click on the smart tag of the grid view again to configure and set the style of header and cells of each columns.

**Templates**

Another nice feature about data-bound controls is that you can customize how the data are displayed using templates. Using templates you can specify the presentation code (HTML) to which the data is bound. For example, for a data field, you might want to display the value in a hyperlink. You can insert a HyperLink control to replace the plain-text Label control.

