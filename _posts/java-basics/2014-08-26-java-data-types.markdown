---
layout: post
status: publish
published: true
title: Java Data and Data Types
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1058
wordpress_url: http://codenuggets.com/?p=1058
date: '2014-08-26 17:15:46 -0500'
date_gmt: '2014-08-26 17:15:46 -0500'
categories:
- Programming
- Java
tags: []
comments:
- id: 3423
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2014-08-27 16:22:22 -0500'
  date_gmt: '2014-08-27 16:22:22 -0500'
  content: "[&#8230;] Step Java Program Basic Structure Java Data and Data Types Java
    [&#8230;]"
- id: 3483
  author: Lamont
  author_email: berthagisborne@gmail.com
  author_url: http://Cecilia.wikispaces.com
  date: '2014-09-07 09:59:58 -0500'
  date_gmt: '2014-09-07 09:59:58 -0500'
  content: "I read a lot of interesting posts here. Probably you  spend a lot of time
    writing, i \r\nknow how to save you a lot of work, there is an online tool that
    creates unique, google friendly posts in seconds, just search in google \r\n-
    k2seotips unlimited content"
- id: 3797
  author: Java Data and Data Types 2 | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/10/22/java-data-and-data-types-2/
  date: '2014-10-22 20:44:39 -0500'
  date_gmt: '2014-10-22 20:44:39 -0500'
  content: "[&#8230;] the previous article, Java Data and Data Types, common data
    types are introduced. Programmers use these types to define variables to track
    states [&#8230;]"
---
In Java, every variable have a type. The reason for variable types is that different kind of data require different amount of memory. For example, a <a href="http://en.wikipedia.org/wiki/Boolean_data_type" target="_blank">boolean</a> variable can only have 1 of 2 values: true or false; therefore, ideally, we only need 1 bit of memory for this type. In contrast, an integer variable can have large number of values, so we many need multiple bytes of memory.

This article explains most commonly used types for declaring variables. If you wish to learn what are variables and how to declaring them, please see the previous article, <a href="http://codenuggets.com/2014/08/09/java-program-structure/" target="_blank">Java Program Basic Structure</a>.

## Integer Numbers

There are 2 kinds of primitive numeric data in Java: integers and decimal point numbers.

The integer types are 

- `byte`: 1 byte or 8 bits
- `short`: 2 bytes or 16 bits
- `int`: 4 bytes or 32 bits
- `long`: 8 bytes or 64 bits

Which one to use depends the requirements of your program. For example, a `byte` take 1 byte of memory, therefore it can only hold a value between -128 and 127; whereas a `short` can hold a value in a larger range.

The following example declares values of type `int`, `byte` and `long`.

{% highlight java %}
int age = 20; //initialize age to 20
byte letter;  //declare a byte and default to 0
long milliseconds; //declare milliseconds to be long
milliseconds = 15000; //assign 15000 to variable milliseconds
{% endhighlight %}

In the example above, `age`, `letter`, and `milliseconds` are variables and `20` and `15000` are called literals.

## Decimal Numbers

The types that represent decimal numbers are:

- `float`: 4 byte or 32 bits
- `double`: 8 bytes or 64 bits

The following code snippet declares a `float` and a `double`. Notice when initializing `price`, there is a a "f" at the end of 1.5. This is because in java, decimal numbers literals are double by default. The suffix "f" signifies this is a float literal.

{% highlight java %}
float price = 1.5f;
double pi = 3.14;
{% endhighlight %}

## Boolean Types

Boolean is a very simple type that can only be either `true` or `false`. Though simple, boolean is a very important type as it is used in flow-control of a program.

The following snippet declares 2 boolean variables.

{% highlight java %}
boolean a;        //default to false
boolean b = true; //declare b and set it to true
boolean c;        //declare c
c = false;        //set c to false
{% endhighlight %}

## Characters and Strings

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

## Arrays

An array is not really a distinct data type, but a list of a type. An array is declared by adding brackets `[]` next to the type. For example, `int[]` declares an array of `int`s. In addition, each elements of a array is accessed by index positions (begin with 0).

The following example declares an array of integers and computes the sum of the array.

{% highlight java %}
int[] myArray = {1, 2, 3};
int sum = myArray[0] + myArray[1] + myArray[2];
{% endhighlight %}

In the above code, notice array can be defined using `{1, 2, 3}` literal. Array values are accessed using `myArray[index]`, where the first index is 0.

### Array Lengh

Java provide us with an easy to get the length of an array. Each array has `length` attribute, which is the number of elements in the array. The following code prints out the length of an array.

{% highlight java %}
int[] myArray = {1, 2, 3};
System.out.println("myArray has size " + myArray.length);

// Output: myArray has size 3
{% endhighlight %}

### When to Use Arrays

Arrays are usually used when a list of variables (memory storage) of the same type is needed and the length is not known when the program is written. This scenario usually arise, when we obtain a data set from an external source and we do not know the size of the data set.

Arrays are usually processed using loops, which will be covered in later articles.

### Array of Arrays

An array of arrays are also called two-dimensional (2-d) arrays. In this array, each element is another array. 2-d arrays are often used to represent a matrix (or a table of values). The following example declares a 3x3 2-d array.

{% highlight java %}
int[][] array = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
{% endhighlight %}