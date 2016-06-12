---
layout: post
status: publish
published: true
title: Communication between parent-child processes using two pipes with C on Linux
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 28
wordpress_url: http://codenuggets.com/?p=28
date: '2012-02-22 02:36:07 -0600'
date_gmt: '2012-02-22 02:36:07 -0600'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
tags:
- Linux
- RDF-3X
- rdf3xquery
- C
- two-way pipes
- process communication
comments:
- id: 3
  author: Adriana
  author_email: cassiatheodoro@hotmail.com
  author_url: http://www.oculosfeminino.com
  date: '2012-02-25 18:35:50 -0600'
  date_gmt: '2012-02-25 18:35:50 -0600'
  content: thanks for share!
- id: 25
  author: Kristofer Benshoof
  author_email: Sickle2269@gmail.com
  author_url: http://www.stnxqvyw.org
  date: '2012-03-19 11:45:36 -0500'
  date_gmt: '2012-03-19 11:45:36 -0500'
  content: I'm still learning from you, while I'm improving myself. I absolutely liked
    reading everything that is posted on your website.Keep the stories coming. I liked
    it!
- id: 54
  author: Cherryl Blyth
  author_email: Cowdrey895@gmail.com
  author_url: http://www.yfkvgeze.org
  date: '2012-04-05 03:28:00 -0500'
  date_gmt: '2012-04-05 03:28:00 -0500'
  content: 'I really like your writing style, good   information,  regards  for  putting
    up : D.'
- id: 78
  author: Darwin Trinka
  author_email: 27Privateer@yahoo.com
  author_url: http://my-burroughs.com/story.php?id=96478
  date: '2012-04-07 21:37:29 -0500'
  date_gmt: '2012-04-07 21:37:29 -0500'
  content: I dugg some of you post as I  cerebrated they were  very helpful   very
    beneficial
- id: 89
  author: Link Building
  author_email: Hain29263@gmail.com
  author_url: http://groups.diigo.com/group/plkylkmlicqrtpuytley/content/raise-the-online-site-s-rankings-with-a-seo-organization-br-br-4153036
  date: '2012-04-08 02:23:38 -0500'
  date_gmt: '2012-04-08 02:23:38 -0500'
  content: I must express my thanks to the writer just for saving me from this situation.
    Right after scouting through the entire internet and being seen tips that were
    not productive, I assumed my well being was gone. Living devoid of the strategies
    to the issues you've sorted out by means of this post is a crucial case, in addition
    to ones which could possess adversely affected my own career if I we had not noticed
    your website.
---
I'm building a system that a system that adds spatial query capabilities on top of RDF-3X, which is a storage and query engine for RDF data. I want to write a layer on top of RDF-3x that takes RDF query involving spatial relationships, rewrite the query, and submit the rewrite queries to the underlying RDF-3x query interface. The design is that RDF-3x query interface will run as a process, and my layer will run as another process that calls the query interface as needed.

I need some mechanism for communication between my process and RDF-3x query interface process. RDF-3x takes a query from the stdin and output query result to stdout. My layer needs to redirect both the stdin and stdout of RDF-3x to itself to submit queries and get results back for processing.

I decided to go with using two pipes for the inter-process communication: one for writing query to the child process (RDF-3x), and the other one for reading result back. I spent about two days figuring out how to do it, and here is my stackoverflow post: <a href="http://stackoverflow.com/questions/9318125/two-way-parent-child-communication-using-2-pipes-in-c-on-linux">http://stackoverflow.com/questions/9318125/two-way-parent-child-communication-using-2-pipes-in-c-on-linux</a>. The point to remember when using a pipe is:

- pipe[0] is the reading end - the end of the pipe data **comes out**
- pipe[1] is the writing end - the end of the pipe data **goes in**

The other issue is about **non-blocking read** of results from RDF-3x. The issues extends from after the query interface returns all the results, it doesn't close the output file descriptor. Since the pipe will always be open, my process doesn't know when the child process returned all the results, and reads in my process will be blocked waiting for more data. I tried to find a way to perform a non-blocking read so that my process simply ends when it sees no more data on the stream, but keep reading when there is more data.

Spent sometime to figure this out and I believe it can definitely be done, but after sometime thinking, blocked read isn't such a bad thing. The reason is that RDF-3x sometimes take a while to return any result. If I had nonblocking read, my process might ended before the results are returned thinking there are no more result.

Instead of using non-blocking read, I modified RDF-3x query interface (rdf3xquery) source code so that the last query result is always followed by a `'\n'` so that when my process sees a new line character, it knows that there are no more result to read.