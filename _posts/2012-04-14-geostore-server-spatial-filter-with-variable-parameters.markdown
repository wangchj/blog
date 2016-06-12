---
layout: post
status: publish
published: true
title: GeoStore Server Spatial Filter with Variable Parameters
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 189
wordpress_url: http://codenuggets.com/?p=189
date: '2012-04-14 17:04:46 -0500'
date_gmt: '2012-04-14 17:04:46 -0500'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
tags: []
comments:
- id: 603
  author: GeoStore Web Client « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2012/05/02/geostore-web-client/
  date: '2012-05-02 20:04:32 -0500'
  date_gmt: '2012-05-02 20:04:32 -0500'
  content: "[...] into RDF triple stores and I'm using RDF-3X as the backend
    triple store. The preview few entries (1, 2) are about the server part of the
    system where our idea of integrating and evaluating spatial [...]"
---
This is an update post on the spatial semantic web GeoStore project. I have made significant progress on the project and the server part (the part that evaluate queries) had reached a milestone and I have implemented all intended queries which are window query, range query, and nearby (knn) query. These queries are explained in <a title="GeoStore Spatial Filters Types" href="http://codenuggets.com/2012/03/27/geostore-spatial-filters-types/" target="_blank">this previous post</a>.

Though all the initial intended aforementioned queries were implemented, there are still a couple more query types or scenarios I'd like to implement and further extend the capability of the query server. You may ask, why implement more queries, which the initial requirements for the paper and the project was already fulfilled? The reason is that <em>the current spatial query filters can only take literal constraints</em>. For example

```
SELECT ?name ?loc
WHERE {
    ?e <name> ?name.
    ?e <location> ?loc.
    within(?loc, 30.1, 29.5, 500)
}
```

Notice the arguments for within() are all literals.

I want to extend the filters so that at least the location argument can take variable bindings. This is useful for queries like find the location of "Auburn High School", and find all gas stations within 2 kilometers radius of it. A sample query of this form would look like

```
SELECT ?name ?loc
WHERE {
    ?auh <name> "Auburn High School".
    ?auh <location> ?center.
    ?e <name> ?name.
    ?e <location> ?loc.
    within(?loc, ?center, 2000)
}
```

In addition, I think it'd be nice to to something with UNION.