---
layout: post
status: publish
published: true
title: Java Variables
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 986
wordpress_url: http://codenuggets.com/?p=986
date: '2014-07-23 04:16:54 -0500'
date_gmt: '2014-07-23 04:16:54 -0500'
categories:
- Programming
- Java
tags: []
comments: []
---
In <a href="http://codenuggets.com/2014/06/20/first-step-in-java/" target="_blank">First Step in Java</a>, we covered how to get started on writing programs using Java. This article introduces a  fundamental concept in computer programming: variables.

## What are Variables?

Let's think about computer games. When you are playing a car racing game, the game must keep track of states of the game, such as time and speed of cars, among others. The game keep track of the states in memory using variables. Simply put, variables are ever-changing states of program in memory.

A program can easily contain a large number of variables; think of all the things the racing game has to track in memory. A computer program really is a sequence of instructions that manipulate its states (variables).

## Types

In Java, every variable have a type. The reason for variable types is that different kind of data require different amount of memory. For example, a <a href="http://en.wikipedia.org/wiki/Boolean_data_type" target="_blank">boolean</a> variable can only have 1 of 2 values: true or false; therefore, ideally, we only need 1 bit of memory for this type. In contrast, an integer variable can have large number of values, so we many need multiple bytes of memory.

The primitive types in Java are: `byte`, `short`, `int`, `long`, `float`, `double`, `boolean`, and `char`. A reference of the completely list with description can be found at the end of this article.

Here we explain most commonly used types.

### Integer Numbers

There are 2 kinds of primitive numeric data in Java: integers and decimal point numbers.

The integer types are 

- `byte`: 1 byte or 8 bits
- `short`: 2 bytes or 16 bits
- `int`: 4 bytes or 32 bits
- `long`: 8 bytes or 64 bits

Which one to use depends the requirements of your program. For example, a `byte` take 1 byte of memory, therefore it can only hold a value between -128 and 127; whereas a `short` can hold a value in a larger range.

Before a variable can be used, it must be declared of its type. The way to declare a variable is `type var_name = init_value;`, where `var_name` can be any name you choose and `init_value` is optional (if not given default value is assigned).

For example the following snippet declares values of type `int`, `byte` and `long`.

{% highlight java %}
int age = 20; //initialize age to 20
byte letter;  //declare a byte and default to 0
long milliseconds; //declare milliseconds to be long
milliseconds = 15000; //assign 15000 to variable milliseconds
{% endhighlight %}

### Decimal Numbers

The types that represent decimal numbers are:

- `float`: 4 byte or 32 bits
- `double`: 8 bytes or 64 bits

The following code snippet declares a `float` and a `double`. Notice when initializing `price`, there is a a "f" at the end of 1.5. This is because in java, decimal numbers literals are double by default. The suffix "f" signifies this is a float literal.

{% highlight java %}
float price = 1.5f;
double pi = 3.14;
{% endhighlight %}

### Boolean Types

Boolean is a very simple type that can only be either `true` or `false`. Though simple, boolean is a very important type as it is used in flow-control of a program.

The following snippet declares 2 boolean variables.

{% highlight java %}
boolean a;        //default to false
boolean b = true; //declare b and set it to true
boolean c;        //declare c
c = false;        //set c to false
{% endhighlight %}

### Characters and Strings

Java also supports textual data, such as character (a single symbol) and strings (multiple characters). Textual types are represented with following types:

- `char`: 16-bit unicode character, such as 'a', '1', '@'
- `String`: multiple `char`

The following snippet shows example of these types. Notice character literals are enclosed in single-quotes, and string literals are enclosed in double-quotes.

{% highlight java %}
char   a = 'a';
char   b = 65;  //unicode 65 which is 'A'
String c = "How's the weather today?";
{% endhighlight %}

### Character Escape

What if we want to assign a single quote to a `char` or include a double quote in a string? Java allows us to include special character using the escape character '\'.

The following snippet illustrates this. A string is enclosed in double quotes, so literals that contains double quotes must be escaped using \.

{% highlight java %}
char   a = '\'';
String b = "He said \"Good day!\"";
{% endhighlight %}

Java have a list of other escape sequences. A list can be found <a href="http://docs.oracle.com/javase/tutorial/java/data/characters.html" target="_blank">here</a>.

## Type Conversion and Casting

Java allows assigning a variable to another variable of a different type. This is called <em>type casting</em>. Generally, if you're assigning a variable to another variable with bigger size in the same family, there is no problem, because the target can accommodate the source (this is called <em>implicit casting</em>). However, if you're assigning a variable of larger size to a variable of smaller size, you're going to get "possible loss of precision error."

For example, in the following code, a `byte` can be safely copied into an `int`, but not so vice versa.

{% highlight java %}
byte b = 123;
int  i = b;   //No problem, 123 is converted to int implicitly
b = i;        //Compiling error: possible loss of precision
{% endhighlight %}

What if we really want to assign a larger type into a smaller type? We can force such conversion through <em>explicit casting</em>, which is done by prefixing (type) to an expression.

{% highlight java %}
byte b = 123;
int  i = 321234;
b = (byte)i;      //Casting content of i to a byte, forcefully
{% endhighlight %}

The following snippet show other casting scenarios.

{% highlight java %}
//int to double is done implicitly
int    age   = 20;
double age_d = age; //age_d contains 20.0

//double to an int is done explicitly
double pi   = 3.14;
int    pi_i = (int)pi; //pi_i contains 3

//Any type can be appended to a string
String a = "pi is equal to " + pi;
{% endhighlight %}

## Reference Types

In addition to the build-in (primitive) types listed above, you can also create your own types, also called compound types, from primitives. Your create reference types by writing a class, which will be covered later. There is no set number reference types because anyone can write a class and create a new type. Commonly used examples are `String`, which is a build-in class, and array of any type.

## Primitive Type Table

The following table shows all primitive types in Java and their capacity.

<table>
<tr>
<th>Type</th>
<th>Description</th>
<th>Range</th>
</tr>
<tr>
<td>byte</td>
<td>8-bit signed two's complement integer</td>
<td>-128 to 127 (inclusive)</td>
</tr>
<tr>
<td>short</td>
<td>16-bit signed two's complement integer</td>
<td>-32,768 to 32,767 (inclusive)</td>
</tr>
<tr>
<td>int</td>
<td>32-bit signed two's complement integer</td>
<td>-2<sup>31</sup> to 2<sup>31</sup>-1 (inclusive)</td>
</tr>
<tr>
<td>long</td>
<td>64-bit signed two's complement integer</td>
<td>-2<sup>63</sup> to 2<sup>63</sup>-1 (inclusive) or 0 to 2<sup>64</sup>-1</td>
</tr>
<tr>
<td>float</td>
<td>single-precision 32-bit IEEE 754 floating point</td>
<td></td>
</tr>
<tr>
<td>double</td>
<td>double-precision 64-bit IEEE 754 floating point</td>
<td></td>
</tr>
<tr>
<td>boolean</td>
<td>two possible values: true and false</td>
<td>true or false</td>
</tr>
<tr>
<td>char</td>
<td>single 16-bit Unicode character</td>
<td>'\u0000' (or 0) to '\uffff' (or 65,535 inclusive)</td>
</tr>
</table>