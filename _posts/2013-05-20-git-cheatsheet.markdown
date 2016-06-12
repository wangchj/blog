---
layout: post
status: publish
published: true
title: Git Cheatsheet
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 514
wordpress_url: http://codenuggets.com/?p=514
date: '2013-05-20 16:27:20 -0500'
date_gmt: '2013-05-20 16:27:20 -0500'
categories:
- Version Control
- Git
tags:
- version control
- git
- cheatsheet
comments: []
---
Commit

<table>
<tr>
<td>Commit with message</td>
<td>git branch -m "Commit Message"</td>
</tr>
</table>
Branching

<table>
<tr>
<td>Create a new branch</td>
<td>git branch [branch name]</td>
</tr>
<tr>
<td>Create and switch to new branch</td>
<td>git checkout -b [branch name]</td>
</tr>
<tr>
<td>Switch branch</td>
<td>git checkout [branch name]</td>
</tr>
</table>
Tags

<table>
<tr>
<td>List tags</td>
<td>git tag</td>
</tr>
<tr>
<td>Create lightweight tag</td>
<td>git tag tag_name</td>
</tr>
<tr>
<td>Delete lightweight tag</td>
<td>git tag -d tag_name</td>
</tr>
<tr>
<td>Push all tags</td>
<td>git push origin --tags</td>
</tr>
</table>
