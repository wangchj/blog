---
layout: post
status: publish
published: true
title: HTML Centered Layout
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 837
wordpress_url: http://codenuggets.com/?p=837
date: '2014-05-25 04:31:21 -0500'
date_gmt: '2014-05-25 04:31:21 -0500'
categories:
- Programming
- HTML
- CSS
tags:
- layout
- align
comments:
- id: 3179
  author: Bette
  author_email: grettacalvin@yahoo.com
  author_url: http://Jan.tumblr.com
  date: '2014-07-14 23:53:01 -0500'
  date_gmt: '2014-07-14 23:53:01 -0500'
  content: "It's hard to find your articles in google. I found it \r\non 20 spot,
    you should build quality backlinks , it will help you to \r\nrank to google top
    10. I know how to help you, just type \r\nin google - k2 seo tips and tricks"
---
A common layout of websites is that the main content of the site does not take the entire width of the browser window and the content is centered on the page. For example, the content of the CNN site is fixed at 1000 pixels in width and centered. The content area can then be organized with sub-layouts or divided into multiple columns. This article describes how to center the HTML block elements on a page using two methods: using `align` attribute, and using CSS margin.

## Using align Attribute

This method can be achieved using two nested `div` elements as shown in the code below. The first `div` sets the `align` attribute to `"center"`. This will set the width of this element to `100%` and center its content.

We may not want all the text inside this layout to be centered, so we have the second `div` inside the first one and resets the `align` attribute to `"left"`.

{% highlight html %}
<div align="center">
    <div align="left">
        Sub-layout and content of the page
    </div>
</div>
{% endhighlight %}

Once we achieved centered layout, the second `div` can be further organized into sub-layout.

In addition, we can also use the `<center>` tag in place of the outer `div`. However, `<center>` is not support in the newer HTML5 standard.

## Using CSS Margin

A block element can be centered by setting its CSS left and right margin to `auto`. This is often done using the shorthand `margin` property as shown below, where the first value sets the <em>top</em> and <em>bottom</em> margins, and the second value sets the <em>left</em> and <em>right</em> margins.

This code causes the browser to set the left and right margins to be the same width expanding the full width of the page and thus centering the content.

{% highlight html %}
<div style="margin:0 auto; width:500px">
    Content to be centered
</div>
{% endhighlight %}

The following much be followed when using this approach:

1. The `div` element must have a width.
2. The `div` element must <em>not</em> float.
