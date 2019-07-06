---
layout: post
status: publish
published: true
title: CSS Three Column Layout
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 846
wordpress_url: http://codenuggets.com/?p=846
date: '2014-06-02 21:03:26 -0500'
date_gmt: '2014-06-02 21:03:26 -0500'
categories:
- Programming
- CSS
tags:
- float
- HTML
- layout
comments: []
---
In previous articles, we explained <a href="http://codenuggets.com/2014/05/14/css-float-explained/" target="_blank">how CSS float allow text to flow around an block element</a> and <a href="http://codenuggets.com/2014/05/22/css-two-column-layout/" target="_blank">how to create two column layout using floats</a>. By columns, we do not mean dividing a long section of text into multiple columns, like in books or research paper. What we mean is dividing a page into columnar sections, where each for different content. In this article, we add one more column and design a three column layout using the floats.

## Float Left and Right

In the article of two column layout, we explain two columns can be created by floating one element and leave the other non-float. In the same token, we can create three columns, by floating two elements, as shown in the figure below.

<img src="/images/figures/css-three-column-layout/two-floats.png" />

{% highlight html %}
<div style="width:420px">
    <div style="float:left; width:100px; height:230px;"></div>
    <div style="float:right; width:100px; height:230px;"></div>
    <div style="margin-left:110px; margin-right:110px; width:200px; height:230px">
</div>
{% endhighlight %}

Three things to consider to make the above layout work:

1. <u>Outer wrapper</u>: because a float is pushed to the edge of its container, a outer wrapper (the first `div`) is used to bring the three elements together. Without the outer div, the right column will be pushed to the edge of the page and leaving too much space between the middle and right columns.
2. <u>Element order</u>: as usual, the float elements have to come before the non-float element.
3. <u>Margins</u>: the middle, non-float, element needs to have enough left and right margins so that its content does not overlap with the content of the float elements.

## Float within Float

Another way two create three columns is to use nested float elements, that is float element within another float element.

In this approach, we first create two columns; then, within one of the two columns, we create another two columns. There are ways (combinations) of floats placement. One combination is shown below.

<img src="/images/figures/css-three-column-layout/nested-floats.png" />

{% highlight html %}
<div style="width:440px">
    <div style="float:left"><!-- Two column wrapper -->
        <div style="float:right; width:200px; height:230px"></div>
        <div style="float:left; width:100px; height:230px;"></div>
    </div>

    <!-- Right column -->
    <div style="float:right;margin-top:10px; width:100px; height:230px;"></div>
</div>
{% endhighlight %}

In this layout, two columns are created by floating one to the left and one to right. Then within the left column, we float the center column right, and left column left.

An advantage of this arrangement over others is that the main, middle, column comes structurally before other columns. This allows (1) for search engines that only reads limited parts of the page to more likely to parse the main content, and (2) screen readers to get the main part before menus and sidebars.