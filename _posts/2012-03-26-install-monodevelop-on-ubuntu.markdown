---
layout: post
status: publish
published: true
title: Install MonoDevelop on Ubuntu
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 106
wordpress_url: http://codenuggets.com/?p=106
date: '2012-03-26 18:12:05 -0500'
date_gmt: '2012-03-26 18:12:05 -0500'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
- Programming
- ".NET"
tags:
- Linux
- Ubuntu
- Mono
- MonoDevelop
comments:
- id: 35
  author: NUnit for MonoDevelop « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2012/03/26/nunit-for-monodevelop/
  date: '2012-03-26 18:45:18 -0500'
  date_gmt: '2012-03-26 18:45:18 -0500'
  content: "[...] the previous post, I wrote about installing MonoDevelop on Ubuntu
    10.04 LTS. This post will be about installing NUnit [...]"
- id: 55
  author: Johnnie Caspers
  author_email: Leitzke2277@gmail.com
  author_url: http://www.maprepgn.com
  date: '2012-04-05 03:55:02 -0500'
  date_gmt: '2012-04-05 03:55:02 -0500'
  content: 'You are my  breathing in, I  have  few  web logs and  infrequently  run
    out from to post  : (.'
- id: 71
  author: london crane hire
  author_email: Paolucci693@yahoo.co.uk
  author_url: http://cranehire.livejournal.com/
  date: '2012-04-07 21:15:18 -0500'
  date_gmt: '2012-04-07 21:15:18 -0500'
  content: I was  examining  some of your posts  on this website  and I think  this  web
    site  is  real   instructive! Keep   putting up.
- id: 80
  author: Alease Liederbach
  author_email: 22Whyman@yahoo.com
  author_url: http://bookmarkgalaxy.com/News/online-poker-free-bonus-no-deposit-via--thx-for-sharing-/
  date: '2012-04-07 21:37:31 -0500'
  date_gmt: '2012-04-07 21:37:31 -0500'
  content: Generally I don't learn article on blogs, however I would like to say that
    this write-up very compelled me to take a look at and do it! Your writing taste
    has been amazed me. Thank you, quite nice article.
- id: 90
  author: Top backlinks
  author_email: Norvell97045@gmail.com
  author_url: http://ernestmcconn36.over-blog.com/pages/google-panda-and-search-engine-optimization-procedures-6877116.html
  date: '2012-04-08 03:57:57 -0500'
  date_gmt: '2012-04-08 03:57:57 -0500'
  content: Greetings from California! I'm bored to death at work and so i decided
    to check out your internet site on my iphone during lunch break. I love the data
    you present right here and can't hold out to take a look when I get home. I'm
    shocked at how quick your blog loaded on my phone, I'm not really even using WIFI,
    just 3G. Anyways, wonderful site!
---
This environment is intended for my spatial RDF store project. The underlying triple store (rdf3xquery) runs on Ubuntu, and my spatial integration are written in C#.

The obvious choice to develop in C# on Ubuntu is to use Mono Framework and <a href="http://monodevelop.com">MonoDevelop</a>. Mono is a cross-platform implementation of the CLI and .NET Framework, and MonDevelop is an IDE designed to use Mono Framework. I check MonoDevelop's website for binary to install, but it appears the binary for Ubuntu is maintained by <a href="http://badgerports.org/">http://badgerports.org/</a>. The following are the steps.

<u>Update</u> (3/31/2012): as of Ubuntu 12.04, MonoDevelop 2.8.3 is included in the official software repository; therefore, there is no need to add badgerport repository.

**Step 1**: Make sure Mono is install, as described <a href="http://codenuggets.com/wp-admin/post.php?post=150&action=edit&message=1"> here</a>

**Step 2**: Add Repository URL

1. Click on "System", "Administration", "Software Sources".
2. Click on the "Other Software" tab.
3. Click on "Add...", and enter the line: `deb http://badgerports.org lucid main`

**Step 3**: Install MonoDevelop in Software Center

The version of Ubuntu I use in this post is 10.04 (LTS), the version of Mono is 2.10.8.1-1, and MonoDevelop is 2.8.6.3+dfsg-2~dhx1~lucid1. 

