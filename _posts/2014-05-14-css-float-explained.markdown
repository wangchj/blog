---
layout: post
status: publish
published: true
title: CSS Float Explained
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 670
wordpress_url: http://codenuggets.com/?p=670
date: '2014-05-14 02:44:37 -0500'
date_gmt: '2014-05-14 02:44:37 -0500'
categories:
- Programming
- CSS
tags:
- float
- HTML
comments:
- id: 2922
  author: CSS Two Column Layout | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/05/22/css-two-column-layout/
  date: '2014-05-22 17:14:02 -0500'
  date_gmt: '2014-05-22 17:14:02 -0500'
  content: "[&#8230;] the previous article, CSS floats were introduced. To recap,
    float elements allow normal flow of the page content to wrap [&#8230;]"
- id: 2995
  author: CSS Three Column Layout | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/06/02/css-three-column-layout/
  date: '2014-06-02 21:26:05 -0500'
  date_gmt: '2014-06-02 21:26:05 -0500'
  content: "[&#8230;] previous articles, we explained how CSS float allow text to
    flow around an block element and how to create two column layout using floats.
    By columns, we do not mean dividing a long [&#8230;]"
---
There are often a bit of mystery on how CSS float work and how they are rendered. Float is a CSS property with the values `left`, `right`, `none`, or `inherit`. When the property is not set, the value is inherited from the parent element.

When the property is set to `none`, the element is rendered according to the <em>normal flow</em> on the page. For inline elements, such as `strong`, `em`, and `span`, the content is rendered on a line of text. For block elements, such as `ul`, and `div`, it is rendered with a line break, then the content of the element.

For example, the following code fragment contains two non-float `div` elements and produces the figure that follows.

{% highlight html %}
<div style="float:none">The first non-float div</div>
<div style="float:none">The second non-float div</div>
{% endhighlight %}

<center><img src="http://codenuggets.com/wp-content/figures/css-float-explained/nonfloat.png"></center>

When the float property is set to either `left` or `right`, the element is taken out of the normal flow, and content that flow normally will wrap around the element.

For example, in the following code fragment, the first `div` floats left, so the second `div`, which is non-float, wraps around the first one.

{% highlight html %}
<div style="float:left; width:100px; border:1px solid green">Lorem Ipsum is simply dummy text of the printing and typesetting industry.
</div>

<div style="float:none; border:1px solid red">Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source.
</div>
{% endhighlight %}

<center><img src="http://codenuggets.com/wp-content/figures/css-float-explained/floats.png"></center>

To illustrate this point further, when a float element is nested inside a non-float element, it is taken out of the layout of the parent element. However, when both the child and the parent are floats, the child is not take out the flow of the parent as shown below.

{% highlight html %}
<div style="border:1px solid green; padding:5px">
    <div style="float:left;width:100px;border:1px solid red">Lorem Ipsum is simply dummy text of the printing and typesetting industry.
    </div>
</div>
{% endhighlight %}

{% highlight html %}
<div style="border:1px solid green; padding:5px">
    <div style="float:left;width:100px;border:1px solid red">Lorem Ipsum is simply dummy text of the printing and typesetting industry.</div>
</div>
{% endhighlight %}

<center><img src="http://codenuggets.com/wp-content/figures/css-float-explained/nested1.png" style="margin-right:20px"> <img src="http://codenuggets.com/wp-content/figures/css-float-explained/nested2.png"></center>

Keep in mind though, the order of the elements matter. Let's say two sibling elements, A and B, with the same parents. A is a float and B is a non-float. B's content would only flow around A if, A's HTML tags comes before B's HTML tags in the source code.

The first code fragment below has a float element that comes after a non-float element, which produced the result on the left. Whereas, the second code fragment has a float element that is place before the non-float element, which produced the result on the right.

{% highlight html %}
<div style="float:none;width:200px;border:1px solid green">Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s
</div>

<div style="float:left;width:200px;border:1px solid red">Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s</div>
{% endhighlight %}

{% highlight html %}
<div style="float:none;width:200px;border:1px solid green">Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s
</div>

<div style="float:left;width:200px;border:1px solid red">Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s</div>
{% endhighlight %}

<center><img src="http://codenuggets.com/wp-content/figures/css-float-explained/order1.png" style="margin-right:20px"> <img src="http://codenuggets.com/wp-content/figures/css-float-explained/order2.png"></center>