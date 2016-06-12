---
layout: post
status: publish
published: true
title: GeoStore Web Client
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 232
wordpress_url: http://codenuggets.com/?p=232
date: '2012-05-02 05:39:38 -0500'
date_gmt: '2012-05-02 05:39:38 -0500'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
- Programming
- ASP.NET
- ".NET"
- C#
- HTML
- CSS
tags:
- Spatial RDF Data
- Google Maps API
comments:
- id: 671
  author: GeoStore Web Client on GitHub « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2012/06/05/geostore-web-client-on-github/
  date: '2012-06-05 03:53:08 -0500'
  date_gmt: '2012-06-05 03:53:08 -0500'
  content: "[...] I decided to create a GitHub repository for the GeoStore Web Client
    project. The reason I create a repository is because I want to integrate Twitter
    Bootstrap into the [...]"
- id: 3335
  author: Valeria
  author_email: mikaylalarry@zoho.com
  author_url: http://Darwin.skyrock.com
  date: '2014-08-11 11:10:43 -0500'
  date_gmt: '2014-08-11 11:10:43 -0500'
  content: "I see you share interesting content here, you can earn some additional
    money, your blog has huge potential, for the monetizing \r\nmethod, just type
    in google - K2 advices \r\nhow to monetize a website"
- id: 3349
  author: bid bond insurance
  author_email: alextraeger@gmx.de
  author_url: https://www.youtube.com/watch?v=L1NrnLYQb50
  date: '2014-08-13 13:17:50 -0500'
  date_gmt: '2014-08-13 13:17:50 -0500'
  content: "Hi there it's me, I am also visiting this web site daily, this web site
    is in fact fastidious and the people are truly sharing fastidious thoughts.\r\n\r\n\r\nFeel
    free to surf to my site ... <a href=\"https://www.youtube.com/watch?v=L1NrnLYQb50\"
    rel=\"nofollow\">bid bond insurance</a>"
- id: 3351
  author: free POS system
  author_email: jeanett.worthington@yahoo.de
  author_url: http://www.youtube.com/watch?v=9eNkVz2GDoQ
  date: '2014-08-13 14:54:57 -0500'
  date_gmt: '2014-08-13 14:54:57 -0500'
  content: "I like what you guys tend to be up too. This sort of clever work and reporting!\r\nKeep
    up the awesome works guys I've incorporated you guys to my personal blogroll."
- id: 3352
  author: dui attorney Bellflower
  author_email: santoslazzarini@googlemail.com
  author_url: https://plus.google.com/b/103461549075697341983/events/c1jme1bvqnskd3k914mt63tqlbs
  date: '2014-08-13 16:32:35 -0500'
  date_gmt: '2014-08-13 16:32:35 -0500'
  content: "May I simply say what a relief to uncover someone who really \r\nunderstands
    what they are discussing over the internet.\r\nYou actually understand how to
    bring an issue to light and make it \r\nimportant. A lot more people really need
    to look at this and understand this \r\nside of your story. I was surprised you
    are not more popular given that you certainly have the gift.\r\n\r\n\r\n\r\nFeel
    free to surf to my blog; <a href=\"https://plus.google.com/b/103461549075697341983/events/c1jme1bvqnskd3k914mt63tqlbs\"
    rel=\"nofollow\">dui attorney Bellflower</a>"
- id: 3358
  author: midwifery Spartanburg
  author_email: veldablackston@gmail.com
  author_url: https://www.youtube.com/watch?v=dxcscmfEQRk
  date: '2014-08-14 11:22:33 -0500'
  date_gmt: '2014-08-14 11:22:33 -0500'
  content: "Thanks  for some other wonderful post. The place else could \r\nanybody
    get that kind of information in such an ideal method of writing?\r\nI have a presentation
    next week, and I am on the search for such information.\r\n\r\nHere is my web
    site; <a href=\"https://www.youtube.com/watch?v=dxcscmfEQRk\" rel=\"nofollow\">midwifery
    Spartanburg</a>"
- id: 3395
  author: banner life insurance rates
  author_email: silasmacghey@yahoo.com
  author_url: https://www.youtube.com/watch?v=479ktWBhv3s
  date: '2014-08-23 06:15:31 -0500'
  date_gmt: '2014-08-23 06:15:31 -0500'
  content: "I do not even know how I ended up here, but I thought this post was good.\r\n\r\nI
    don't know who you are but definitely you're going to a famous blogger if you
    aren't already ;) Cheers!"
- id: 3398
  author: Zamurai PBN Blueprint
  author_email: annett_gourgaud@yahoo.de
  author_url: http://www.youtube.com/watch?v=qdDgB5EhsMY&feature=share
  date: '2014-08-24 05:34:29 -0500'
  date_gmt: '2014-08-24 05:34:29 -0500'
  content: "Its not my first time to visit this web page, i am visiting this web page
    dailly and take pleasant data from here \r\ndaily.\r\n\r\nMy web blog; <a href=\"http://www.youtube.com/watch?v=qdDgB5EhsMY&feature=share\"
    rel=\"nofollow\">Zamurai PBN Blueprint</a>"
---
For the past few weeks, I've been working on the client side of my research project. To recap, the research is to integrate geospatial query filtering capabilities into RDF triple stores and I'm using <a href="http://www.mpi-inf.mpg.de/~neumann/rdf3x/">RDF-3X</a> as the backend triple store. The preview few entries (<a href="http://codenuggets.com/2012/04/14/geostore-server-spatial-filter-with-variable-parameters/">1</a>, <a href="http://codenuggets.com/2012/03/27/geostore-spatial-filters-types/">2</a>) are about the server part of the system where our idea of integrating and evaluating spatial capabilities are implemented. The server is mostly done, so I've moved to the client part, which submits a query to the server and obtain the results.

For the client, I decided to make it web-based (a website). The server talks through TCP/IP connection, so the client doesn't have to be web-based. The reason I choose to implement a web-based client is that I want to integrate a map into the interface for the user to build geospatial query filters. The most simple map library is <a href="https://developers.google.com/maps/documentation/javascript/">Google Maps API</a> and it's primarily web-based interfaced via JavaScript. I'm been working tremendously with JavaScript which is good for me to learn more advanced features of the language, and I have been very satisfied with the Maps API with its good documentation and ease of use.

## Query Builder

Currently, the query builder of the client looks like the following figure.

<a href="http://codenuggets.com/wp-content/uploads/2012/05/sparql_spatial_query_builder.png"><img src="http://codenuggets.com/wp-content/uploads/2012/05/sparql_spatial_query_builder.png" alt="" title="sparql_spatial_query_builder" width="550" /></a>

The client interface is divided into 3 parts. The first part is a SPARQL query editor, where user can type in the SPARQL query. The second part is the query builder where parameters of query pattern and spatial query filters can be built. The geographic regions on the map in the figure above can be interpreted as filtering the query results to within 1km from Auburn Library, 2km from Auburn High School, and within the rectangular region between Thach Ave and Opelika Road. After the user click on the Insert button of the query builder, a pattern or a filter is inserted into the editor. The third and final part of the interface are the sample queries which are listed under the query builder.

