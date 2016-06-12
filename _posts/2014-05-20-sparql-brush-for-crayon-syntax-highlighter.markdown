---
layout: post
status: publish
published: true
title: SPARQL Brush for Crayon Syntax Highlighter
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 799
wordpress_url: http://codenuggets.com/?p=799
date: '2014-05-20 03:18:26 -0500'
date_gmt: '2014-05-20 03:18:26 -0500'
categories:
- Programming
- Wordpress
tags:
- SPARQL
- syntax highlight
comments: []
---
This is a syntax brush I have created for the <a href="http://en.wikipedia.org/wiki/SPARQL" target="_blank">SPARQL</a> for the <a href="https://github.com/aramk/crayon-syntax-highlighter" target="_blank">Crayon Syntax Highlighter</a>. The brush recognizes the following elements:

1. Reserved words: such as `SELECT`, `WHERE`</li>
2. Resources (IRI): such as `<http://codenuggets.com/jeff>` or `<Given_Name>`, which are currently recognized as strings.</li>
3. Quoted string literals: such as `"Johnny"`</li>
4. Varaibles: such as `$name`

## Sample

Use the brush name `sparql` to highlight SPARQL code blocks. A sample code block follows.

{% highlight sql %}
PREFIX a: <http://www.w3.org/2000/10/annotation-ns#>
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>

# Comment!

SELECT ?given ?family
WHERE {
  ?annot a:annotates <http://www.w3.org/TR/rdf-sparql-query/> .
  ?annot dc:creator ?c .
  OPTIONAL {?c foaf:given ?given ;
               foaf:family ?family } .
  FILTER isBlank(?c)
}
{% endhighlight %}

## Installation

The source code of this brush is hosted on <a href="https://github.com/wangchj/crayon-highlighter-sparql-brush">GitHub</a>. To install, download and unzip in the `lang` directory of Crayon.

```
cd wordpress/wp-content/plugins/crayon/lang
wget https://github.com/wangchj/crayon-highlighter-sparql-brush/archive/master.zip
unzip crayon-highlighter-sparql-brush-master.zip
mv crayon-highlighter-sparql-brush-master sparql
```

Alternatively, you may also clone the git repository.

