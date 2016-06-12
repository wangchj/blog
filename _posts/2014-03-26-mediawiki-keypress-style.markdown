---
layout: post
status: publish
published: true
title: MediaWiki Keypress Style
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 636
wordpress_url: http://codenuggets.com/?p=636
date: '2014-03-26 16:49:51 -0500'
date_gmt: '2014-03-26 16:49:51 -0500'
categories:
- Programming
- Shortwiki
tags:
- CSS
- MediaWiki
- key press style
- Wikipedia
comments: []
---
The following are the list of customizations for Shortwiki to have Keypress style of Wikipedia. These should probably be checked into a source control, but I just started working on this project, and MediaWiki, so I'm just jotting down some notes. I'll organize theses more after I get a feeling of how MediaWiki work.

1\. Put the following in skins/common/commonElements.css

{% highlight css %}kbd {
    border: 1px solid #aaa;
    -moz-border-radius: 0.2em;
    -webkit-border-radius: 0.2em;
    border-radius: 0.2em;
    -moz-box-shadow: 0.1em 0.2em 0.2em #ddd;
    -webkit-box-shadow: 0.1em 0.2em 0.2em #ddd;
    box-shadow: 0.1em 0.2em 0.2em #ddd;
    background-color: #f9f9f9;
    background-image: -moz-linear-gradient(top, #eee, #f9f9f9, #eee);
    background-image: -o-linear-gradient(top, #eee, #f9f9f9, #eee);
    background-image: -webkit-linear-gradient(top, #eee, #f9f9f9, #eee);
    background-image: linear-gradient(to bottom, #eee, #f9f9f9, #eee);
    padding: 0.1em 0.3em;
    font-family: inherit;
    font-size: 0.85em;
}
{% endhighlight %}
Note: this is the style of Keyboard keys used in Wikipedia.

2\. Copy the following pages from Wikipedia:

- Template:Unicode
- Template:Key press
- Template:Key press/core
- Template:Documentation

3\. Redirect page Template:Keypress to Template:Key press

4\. Enable ParserFunctions extension by adding the following to LocalSettings.php

{% highlight php %}
require_once("$IP/extensions/ParserFunctions/ParserFunctions.php");
{% endhighlight %}

References:

1. <a href="http://www.mediawiki.org/wiki/Thread:Project:Support_desk/How_to_include_Keypress_in_wiki">How to include Keypress in wiki</a>
2. <a href="http://www.mediawiki.org/wiki/Help:Extension:ParserFunctions">Help:Extension:ParserFunctions</a>