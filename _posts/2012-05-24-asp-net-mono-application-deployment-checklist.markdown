---
layout: post
status: publish
published: true
title: ASP.NET Mono Application Deployment Checklist
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 287
wordpress_url: http://codenuggets.com/?p=287
date: '2012-05-24 19:46:02 -0500'
date_gmt: '2012-05-24 19:46:02 -0500'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
- Programming
- ASP.NET
- ".NET"
tags:
- Linux
- ASP.NET
- Ubuntu
- Mono
- Apache
- mod_mono
- checklist
comments: []
---

## 1. Use the latest Mono Framework

Especially you're using latest version of .NET Framework in your application. See <a href="">this post</a> on upgrading Mono.

## 2. File name case-sensitivity

File names on Windows are not case-sensitive but on Linux (and Mac OS X), they are. It's a good practice to match the name of the file in other files you're referencing the file.

For example, in ASP.NET, template files are often named `Site.Master`, but referenced as `Site.master`. The references should be changed to `Site.Master` or change the file name to `Site.master`.

## 3. Remove requestValidationMode

`requestValidationMode` in Web.config does not work. If you have the following in the `<system.web>`, it should be removed.

{% highlight xml %}
<httpRuntime requestValidationMode="2.0"/>
{% endhighlight %}


