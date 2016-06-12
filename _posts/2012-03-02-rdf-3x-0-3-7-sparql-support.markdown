---
layout: post
status: publish
published: true
title: RDF-3X (0.3.7) SPARQL Support
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 74
wordpress_url: http://codenuggets.com/?p=74
date: '2012-03-02 20:48:23 -0600'
date_gmt: '2012-03-02 20:48:23 -0600'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
tags:
- RDF-3X
- rdf3xquery
comments:
- id: 47
  author: Marlys Perlow
  author_email: Lively552@gmail.com
  author_url: http://www.stnxqvyw.org
  date: '2012-04-04 18:54:50 -0500'
  date_gmt: '2012-04-04 18:54:50 -0500'
  content: Very nice info and right to the point. I am not sure if this is truly the
    best place to ask but do you people have any ideea where to employ some professional
    writers? Thanks in advance :)
- id: 83
  author: Todd Schinkel
  author_email: 99Tolefree@yahoo.com
  author_url: http://share.eyakka.com/story.php?id=17840
  date: '2012-04-07 21:37:34 -0500'
  date_gmt: '2012-04-07 21:37:34 -0500'
  content: Thanks, I've recently been searching for info about this topic for a while
    and yours is the best I've discovered so far. However, what about the conclusion?
    Are you sure in regards to the supply?
- id: 85
  author: Page Chauncey
  author_email: Stant40224@yahoo.com
  author_url: http://indiahottrends.com/
  date: '2012-04-07 21:58:41 -0500'
  date_gmt: '2012-04-07 21:58:41 -0500'
  content: Hello, just wanted to tell you, I liked this article. It was funny. Keep
    on posting!
---
Source code of RDF-3X can be obtained from <a href="http://code.google.com/p/rdf3x/">RDF-3X Google Code Repository</a>.

A summary of SPARQL support of RDF-3X based on my own testing.

**Query Types**

<table>
<tbody>
<tr>
<td>Query Type</td>
<td>Example</td>
<td>Support</td>
</tr>
<tr>
<td>SELECT</td>
<td>SELECT ?a WHERE{?a <name> "Jeff"}</td>
<td>Yes</td>
</tr>
<tr>
<td>ASK</td>
<td>ASK ?a WHERE{?a <name> "Jeff"}</td>
<td>No</td>
</tr>
<tr>
<td>DESCRIBE</td>
<td>DESCRIBE <http://www.facebook.com/johndoe></td>
<td>No</td>
</tr>
<tr>
<td>CONSTRUCT</td>
<td></td>
<td>No</td>
</tr>
</tbody>
</table>
**Projection**

<table>
<tbody>
<tr>
<td>Feature</td>
<td>Example</td>
<td>Support</td>
</tr>
<tr>
<td>DISTINCT</td>
<td>SELECT DISTINCT ?a WHERE{?a <name> "Jeff"}</td>
<td>Yes</td>
</tr>
<tr>
<td>Expressions</td>
<td>SELECT (1+1)</td>
<td>No</td>
</tr>
<tr>
<td>LIMIT</td>
<td>SELECT ?url WHERE{?url <name> "Jeff"} <b>LIMIT 10</b></td>
<td>Yes</td>
</tr>
<tr>
<td>OFFSET</td>
<td>SELECT ?url WHERE{?url <name> "Jeff"} OFFSET 10</td>
<td>No</td>
</tr>
<tr>
<td>ORDER BY</td>
<td>SELECT ?url ?age WHERE{?url <name> "Jeff". ?url <age> ?age} <b>ORDER BY ?age</b></td>
<td>Yes</td>
</tr>
</tbody>
</table>
**Graph Pattern**

<table>
<tbody>
<tr>
<td>Feature</td>
<td>Example</td>
<td>Support</td>
</tr>
<tr>
<td>UNION</td>
<td>SELECT ?name<br />
WHERE {?e <name> ?name. {?e <type> "actor"} <b>UNION</b> {?e <type> "athlete"}}</td>
<td>Yes</td>
</tr>
</tbody>
</table>