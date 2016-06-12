---
layout: post
status: publish
published: true
title: CSS Two Column Layout
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 667
wordpress_url: http://codenuggets.com/?p=667
date: '2014-05-22 17:13:54 -0500'
date_gmt: '2014-05-22 17:13:54 -0500'
categories:
- Programming
- CSS
tags:
- CSS
- float
- columns
comments: []
---
In the <a href="http://codenuggets.com/2014/05/14/css-float-explained/">previous article</a>, CSS floats were introduced. To recap, float elements allow normal flow of the page content to wrap around them, much like text that wraps around pictures in magazines.

In addition to allowing content to wrap around certain elements, float are also the most accepted way to create columns on a web page. By columns, I do not mean dividing a section of long text into columns as in novels, but displaying different parts of a page side-by side. For example, a side bar and main content in different columns. Traditionally `table` elements were used to create columns, but this article we focus using CSS and block elements, such as `div`s.

## Making Columns

The easiest way to create two columns is to float one `div` element and leave the other non-float. As stated in <a href="http://codenuggets.com/2014/05/14/css-float-explained/" target="_blank">CSS Float Explained</a>, the float element is taken out of the normal float, so the box of the non-float element may overlap with the float element and not give us the column layout.

There are two ways to fix this problem:

1. Make the non-float element wide enough to clear the float element
2. Give the non-float element enough margin to push it clear the float element

Consider these examples:

1\. The elements in the figure below have the same width. Since the box of both elements overlap, the content of the non-float (2nd) element gets push below the float element. Note: the float element has dashed border, and non-float element has solid border.

{% highlight html %}
<div style="
	float:left;
	width:250px;
	margin:2px;
	padding:2px;
	border:1px dashed black">
	Lorem Ipsum is ...
</div>
<div style="
	width:250px;
	border:1px solid black;
	padding:5px">Lorem Ipsum is ...
</div>
{% endhighlight %}

<img src="http://codenuggets.com/wp-content/figures/css-columns/overlap-box.png" />

2\. <u>Expand the width</u> of the non-float element so that there is enough space for text to be placed next to the float element, as shown in the first figure. The problem with this approach is that when the text gets longer, it gets wrapped below the float element, as in second figure.

{% highlight html %}
<div style="
	float:left;
	width:250px;
	margin:2px; margin-right:10px;
	padding:2px;
	border:1px dashed black">
	Lorem Ipsum is ...
</div>
<div style="
	width:500px;
	border:1px solid black;
	padding:5px">Lorem Ipsum is ...
</div>
{% endhighlight %}

<img src="http://codenuggets.com/wp-content/figures/css-columns/expand-width-1.png" />

<img src="http://codenuggets.com/wp-content/figures/css-columns/expand-width-2.png" />

3\. <u>Expand the margin</u> of the non-float element to clear the float element as shown in the figure below.
Although, the content of the non-float element completely clears the float element, their boxes still overlap. The pink area in the figure represents the margins and blue the content area of the non-float element. Clearly, the two `divs`s still overlap. But without the borders, they appear as two columns to viewers.

{% highlight html %}
<div style="
	float:left;
	width:250px;
	margin:2px;
	padding:2px;
	border:1px dashed black">
	Lorem Ipsum is ...
</div>
<div style="
	width:250px;
	margin-left:270px;
	border:1px solid black;
	padding:2px">Lorem Ipsum is ...
</div>
{% endhighlight %}

<img src="http://codenuggets.com/wp-content/figures/css-columns/wide-margin.png" />

Generally, using the margin, as shown in this example, is the best way to create columns in CSS.

## Multiple Floats

In addition to mixing float and non-float elements, we can also float both elements to create the columns layout. In this case all we need to change is add `float:left` to the original non-float element.
	
One thing to watch out for is the <u>float drop</u>, as shown below. This situation happens when the parent container of the floats don't have enough space. The fix for this is to increase the width of the parent container.

<img src="http://codenuggets.com/wp-content/figures/css-columns/drop.png" />