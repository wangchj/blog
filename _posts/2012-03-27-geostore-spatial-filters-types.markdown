---
layout: post
status: publish
published: true
title: GeoStore Spatial Filters Types
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 124
wordpress_url: http://codenuggets.com/?p=124
date: '2012-03-27 17:52:21 -0500'
date_gmt: '2012-03-27 17:52:21 -0500'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
tags: []
comments:
- id: 82
  author: Phung No
  author_email: 5Gamotan@yahoo.com
  author_url: http://breakthrough.org.ua/story.php?id=77876
  date: '2012-04-07 21:37:33 -0500'
  date_gmt: '2012-04-07 21:37:33 -0500'
  content: Usually I do not learn post on blogs, however I wish to say that this write-up
    very forced me to check out and do so! Your writing style has been surprised me.
    Thank you, quite great article.
- id: 579
  author: GeoStore Server Spatial Filter with Variable Paramenters « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2012/04/14/geostore-server-spatial-filter-with-variable-paramenters/
  date: '2012-04-14 17:04:54 -0500'
  date_gmt: '2012-04-14 17:04:54 -0500'
  content: "[...] This is an update post on the spatial semantic web GeoStore project.
    I have made significant progress on the project and the server part (the part
    that evaluate queries) had reached a milestone and I have implemented all intended
    queries which are window query, range query, and nearby (knn) query. These queries
    are explained in this previous post. [...]"
- id: 602
  author: GeoStore Web Client « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2012/05/02/geostore-web-client/
  date: '2012-05-02 20:00:50 -0500'
  date_gmt: '2012-05-02 20:00:50 -0500'
  content: "[...] RDF triple stores and I'm using RDF-3X as the backend triple
    store. The preview few entries (1, 2) are about the server part of the system
    where our idea of integrating and evaluating spatial [...]"
---
For the last couple of weeks, I've still been working on my research project of integrating spatial filters into RDF3X triple store. In particular, I've been working on the server side of the project, which takes queries from the client side, analyze and execute them, and return result back to the client. For my convenience of referencing the project, I decided to call it "GeoStore", instead of "Spatial Function Triple Store Integration" (Ins't that easier?).

The following are the spatial filters types I implement in the system and some descriptions.

<table>
<tbody>
<tr>
<td>Filter Name</td>
<td>Syntax Name</td>
<td>Args</td>
<td>Description</td>
</tr>
<tr>
<td>Window</td>
<td>within</td>
<td>5</td>
<td>Filters results to a rectangular region</td>
</tr>
<tr>
<td>Range</td>
<td>within</td>
<td>4</td>
<td>Filters results to within a distance from a point</td>
</tr>
<tr>
<td>NearBy</td>
<td>nearby</td>
<td>4</td>
<td>Filters results to k nearest to a point</td>
</tr>
</tbody>
</table>

## Window Filter

<h3>Syntax</h3>
within(?var, xmin, ymin, xmax, ymax)

<h3>Parameters</h3>
?var query variable to be filteredxminNumericx coordinate of lower-left corner of the rectangle

<table>
<tbody>
<tr>
<td>Param</td>
<td>Type</td>
<td>Description</td>
</tr>
<tr>
<td>xmin</td>
<td>Numeric</td>
<td>x coordinate of lower-left corner of the rectangle</td>
</tr>
</tr>
<tr>
<td>ymin</td>
<td>Numeric</td>
<td>y coordinate of lower-left corner of the rectangle</td>
</tr>
<tr>
<td>xmax</td>
<td>Numeric</td>
<td>x coordinate of upper-right corner of the rectangle</td>
</tr>
<tr>
<td>ymax</td>
<td>Numeric</td>
<td>y coordinate of upper-right corner of the rectangle</td>
</tr>
</tbody>
</table>
<a href="http://codenuggets.com/wp-content/uploads/2012/03/WindowQuery.png"><img src="http://codenuggets.com/wp-content/uploads/2012/03/WindowQuery-150x150.png" alt="Window Query Filter" title="Window Query Filter" width="150" height="150" class="size-thumbnail wp-image-169" /></a> Window Query Filter

## Range Filter

<h3>Syntax</h3>
within(?var, x, y, rangeMeters)

<h3>Parameters</h3>
?var query variable to be filteredxNumericx coordinate of center

<table>
<tbody>
<tr>
<td>Param</td>
<td>Type</td>
<td>Description</td>
</tr>
<tr>
<td>x</td>
<td>Numeric</td>
<td>x coordinate of center</td>
</tr>
</tr>
<tr>
<td>y</td>
<td>Numeric</td>
<td>y coordinate of center</td>
</tr>
<tr>
<td>rangeMeters</td>
<td>Numeric</td>
<td>radius in meters</td>
</tr>
</tbody>
</table>
<a href="http://codenuggets.com/wp-content/uploads/2012/03/RangeQueryFilter.png"><img src="http://codenuggets.com/wp-content/uploads/2012/03/RangeQueryFilter-150x150.png" alt="Range Query Filter" title="Range Query Filter" width="150" height="150" class="size-thumbnail wp-image-171" /></a> Range Query Filter

## NearBy Filter

<h3>Syntax</h3>
nearby(?var, x, y, limit)

<h3>Parameters</h3>
?var query variable to be filteredxNumericx coordinate of point

<table>
<tbody>
<tr>
<td>Param</td>
<td>Type</td>
<td>Description</td>
</tr>
<tr>
<td>x</td>
<td>Numeric</td>
<td>x coordinate of point</td>
</tr>
<tr>
<td>y</td>
<td>Numeric</td>
<td>y coordinate of point</td>
</tr>
<tr>
<td>limit</td>
<td>Integer</td>
<td>number of nearest records to return</td>
</tr>
</tbody>
</table>