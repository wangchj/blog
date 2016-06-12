---
layout: post
status: publish
published: true
title: Java Boolean Expressions
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1173
wordpress_url: http://codenuggets.com/?p=1173
date: '2014-12-27 21:44:50 -0600'
date_gmt: '2014-12-27 21:44:50 -0600'
categories:
- Programming
- Java
tags:
- operators
- logic
- comparison
- boolean
- operator precedence
comments:
- id: 4128
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-01 02:06:09 -0600'
  date_gmt: '2015-01-01 02:06:09 -0600'
  content: "[&#8230;] Data and Data Types Java Classes and Objects Java Arithmetic
    Operators Java Data and Data Types 2 Java Boolean Expressions Java If and Else
    Java [&#8230;]"
---
Java's arithmetic operators, such as `+`, `-`, `*`, `/`, perform calculations on numeric data types and return a numeric value and are the building blocks of arithmetic expressions. In this article, we cover another category of operations that perform logical comparisons. Logical operators are the building blocks of boolean expressions, which can be evaluated to a boolean value that is either `true` or `false`.

As you can imagine, boolean expression are useful for branching statements in our program. For example, if certain boolean condition is true, our program should do this; otherwise, the program should do something else. In fact, boolean expressions are used in conditional statements, such as `if-else` statement, and looping statements, such as `while` loop. These control statements will be covered in succeeding articles.

## Comparison Operators

A simple true-false expression is just comparing two things. Do do so, we use Java's comparison operators below, assuming `a = 3` and `b = 4`.

<table style="text-align:center">
<tr>
<th>Operator</th>
<th>Meaning</th>
<th>Example</th>
</tr>
<tr>
<td>==</td>
<td>equal to</td>
<td>`a == b` is false</td>
</tr>
<tr>
<td>!=</td>
<td>not equal to</td>
<td>`a != b` is true</td>
</tr>
<tr>
<td><</td>
<td>less than</td>
<td>`a < b` is true</td>
</tr>
<tr>
<td><=</td>
<td>less than or equal to</td>
<td>`a <= b` is true</td>
</tr>
<tr>
<td>></td>
<td>greater than</td>
<td>`b > b` is false</td>
</tr>
<tr>
<td><=</td>
<td>greater than or equal to</td>
<td>`b <= b` is true</td>
</tr>
</table>
These comparison operators can be used for all built-in data types and behave as expected most of the time. One must be very careful when comparing a variable of float-point type (float and double) against a literal, due to <a href="https://books.google.com/books?id=lbnjAwAAQBAJ&pg=PA149&dq=java+float+equality&hl=en&sa=X&ei=-w2fVKPYAYurgwSy04O4Cg&ved=0CB0Q6AEwAA#v=onepage&q=java%20float%20equality&f=false">impreciseness of float-point encoding</a>.

These operators can also be used to compare variable of <a href="http://codenuggets.com/2014/10/22/java-data-and-data-types-2/">reference types</a> (objects); however, when used, these operators performs reference (address) comparison. For example, given two objects `a` and `b`, `a == b` is true only if `a` and `b` are the same object in memory, regardless of object's content. For this reason, objects are usually compared using <a href="http://codenuggets.com/2014/06/24/java-equals-method/">`equals()`</a> method, or using implementation of <a href="http://codenuggets.com/2014/06/29/java-comparable-interface/">`Comparable`</a> and <a href="http://codenuggets.com/2014/06/29/java-comparator/">`Comparator`</a> interfaces.

## Logical Operators

In addition, Java has following logical operators.

<table style="text-align:center">
<tr>
<th>Operator</th>
<th>Meaning</th>
<th>True if</th>
<th>Example</th>
</tr>
<tr>
<td>!</td>
<td>not</td>
<td>operand is not true (truth reversal)</td>
<td>`(!true)` is false</td>
</tr>
<tr>
<td>&&</td>
<td>and</td>
<td>both operands are true</td>
<td>`(true && false)` is false</td>
</tr>
<tr>
<td>||</td>
<td>or</td>
<td>one or both operand is true</td>
<td>`(true || false)` is true</td>
</tr>
<tr>
<td>^</td>
<td>xor</td>
<td>only one operand is true, not both</td>
<td>`(true || true)` is false</td>
</tr>
</table>
## Examples

{% highlight java %}
public class BooleanExpressionExample
{
    public static void main(String[] args)
    {
        int a = 1;
        int b = 2;
        boolean x = false;

        x = a > 0 && b > a;    //x -> true
        x = a > 0 && b < a;    //x -> false
        x = a > 0 || b < a;    //x -> true
        x = (a > 0) ^ (b > a); //x -> false
        x = (a > 0) ^ (b < a); //x -> true
        x = (a < 0) ^ (b < a); //x -> false
    }
}
{% endhighlight %}

## Operator Precedence

The following list is the order of operation of conditional operators, top ones before bottom ones.

<table style="text-align:center">
<tr>
<th>Operator</th>
<th>Description</th>
</tr>
<tr>
<td>!</td>
<td>not</td>
</tr>
<tr>
<td>==, !=</td>
<td>equality</td>
</tr>
<tr>
<td>^</td>
<td>xor</td>
</tr>
<tr>
<td>&&</td>
<td>and</td>
</tr>
<tr>
<td>||</td>
<td>or</td>
</tr>
<tr>
<td>=</td>
<td>assignment</td>
</tr>
</table>
For a complete list of operators and their precedence please see <a href="http://codenuggets.com/2015/01/04/java-operator-precedence/">Java Operator Precedence</a>. 

