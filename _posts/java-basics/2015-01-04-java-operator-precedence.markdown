---
layout: post
status: publish
published: true
title: Java Operator Precedence
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1251
wordpress_url: http://codenuggets.com/?p=1251
date: '2015-01-04 05:59:25 -0600'
date_gmt: '2015-01-04 05:59:25 -0600'
categories:
- Programming
- Java
tags:
- Java
- operators
comments:
- id: 4135
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-04 06:00:19 -0600'
  date_gmt: '2015-01-04 06:00:19 -0600'
  content: "[&#8230;] Classes and Objects Java Arithmetic Operators Java Data and
    Data Types 2 Java Boolean Expressions Java Operator Precedence Java If and Else
    Java Loops Java [&#8230;]"
---
The following table is a list all operators and their **precedence** (order of evaluation). Operators with lower level are performed before higher level.

Operators in the same level are evaluated either from left to right or right to left, which is described by **associativity**. For example, assignment operator (`=`) have right-to-left associativity; therefore, the expression at the right of the operator is evaluated first, then assigned to the the variable at the left of the operator.

Programmers don't have to remember the exact precedence. Instead, **parentheses** can be used to enforce the order of evaluation.

<table style="text-align:center">
    <tr>
        <th>Operator</th>
        <th>Description</th>
        <th>Level</th>
        <th>Associativity</th>
    </tr>
    <tr>
        <td>
            <tt>[]</tt><br><br />
            <tt>.</tt><br><br />
            <tt>()</tt><br><br />
            <tt>++</tt><br><br />
            <tt>--</tt>
        </td>
        <td>
            access array element<br><br />
            access object member<br><br />
            invoke a method<br><br />
            post-increment<br><br />
            post-decrement
        </td>
        <td>1</td>
        <td>left to right</td>
    </tr>
    <tr>
        <td>
            <tt>++</tt><br><br />
            <tt>--</tt><br><br />
            <tt>+</tt><br><br />
            <tt>-</tt><br><br />
            <tt>!</tt><br><br />
            <tt>~</tt>
        </td>
        <td>
            pre-increment<br><br />
            pre-decrement<br><br />
            unary plus<br><br />
            unary minus<br><br />
            logical NOT<br><br />
            bitwise NOT
        </td>
        <td>2</td>
        <td>right to left</td>
    </tr>
    <tr>
        <td>
            <tt>()</tt><br><br />
            <tt>new</tt>
        </td>
        <td>
            cast<br><br />
            object creation
        </td>
        <td>3</td>
        <td>right to left</td>
    </tr>
    <tr>
        <td>
            <tt>*</tt><br><br />
            <tt>/</tt><br><br />
            <tt>%</tt>
        </td>
        <td>
            multiplication<br><br />
            division<br><br />
            modulus
        </td>
        <td>4</td>
        <td>left to right</td>
    </tr>
    <tr>
        <td>
            <tt>+</tt><br><br />
            <tt>-</tt>
        </td>
        <td>
            addition, string concatenation<br><br />
            subtraction
        </td>
        <td>5</td>
        <td>left to right</td>
    </tr>
    <tr>
        <td>
            <tt><<</tt><br><br />
            <tt>>></tt><br><br />
            <tt>>>></tt>
        </td>
        <td>
            left shift<br><br />
            right shift<br><br />
            unsigned right shift
        </td>
        <td>6</td>
        <td>left to right</td>
    </tr>
    <tr>
        <td>
            <  <br><br />
            <= <br><br />
            >  <br><br />
            >= <br><br />
            <tt>instanceof</tt>
        </td>
<td>
            less than<br><br />
            less than or equal to<br><br />
            greater than<br><br />
            greater than or equal to<br><br />
            type comparison
        </td>
<td>7</td>
<td>left to right</td>
</tr>
<tr>
<td>
            <tt>==</tt><br><br />
            <tt>!=</tt>
        </td>
<td>
            equality
        </td>
<td>8</td>
<td>left to right</td>
</tr>
<tr>
<td><tt>&</tt></td>
<td>bitwise AND</td>
<td>9</td>
<td>left to right</td>
</tr>
<tr>
<td><tt>^</tt></td>
<td>bitwise XOR</td>
<td>10</td>
<td>left to right</td>
</tr>
<tr>
<td><tt>|</tt></td>
<td>bitwise OR</td>
<td>11</td>
<td>left to right</td>
</tr>
<tr>
<td><tt>&&</tt></td>
<td>conditional AND</td>
<td>12</td>
<td>left to right</td>
</tr>
<tr>
<td><tt>||</tt></td>
<td>conditional OR</td>
<td>13</td>
<td>left to right</td>
</tr>
<tr>
<td><tt>?:</tt></td>
<td>conditional</td>
<td>14</td>
<td>right to left</td>
</tr>
<tr>
<td>
            =    <br><br />
            +=   <br><br />
            -=   <br><br />
            *=   <br><br />
            /=   <br><br />
            %=   <br><br />
            &=   <br><br />
            ^=   <br><br />
            |=   <br><br />
            <<=  <br><br />
            >>=  <br><br />
            >>>= <br>
        </td>
<td>
            assignment
        </td>
<td>15</td>
<td>right to left</td>
</tr>
</table>
