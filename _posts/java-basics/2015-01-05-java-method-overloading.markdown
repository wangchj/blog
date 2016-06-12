---
layout: post
status: publish
published: true
title: Java Method Overloading
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1276
wordpress_url: http://codenuggets.com/?p=1276
date: '2015-01-05 05:25:47 -0600'
date_gmt: '2015-01-05 05:25:47 -0600'
categories:
- Programming
- Java
tags: []
comments:
- id: 4155
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-07 18:08:54 -0600'
  date_gmt: '2015-01-07 18:08:54 -0600'
  content: "[&#8230;] Data and Data Types 2 Java Boolean Expressions Java Operator
    Precedence Java If and Else Java Loops Java Method Overloading Java Constructor
    Java [&#8230;]"
---
Previously we covered the basics of writing classes and method in <a href="http://codenuggets.com/2014/11/07/java-classes-and-objects/">this</a> article. Because object-oriented-programming (OOP) concepts are such an important topic in Java, we're coming back to covering the rich OOP features offered by Java! In this article we are going to start slow and cover the simple topic of method overloading.

## Method Overloading

Method overloading is to have multiple methods having the same name but different parameter list. When we say the same parameter list we mean the same number of parameters, with the same types, in the same orders. It's intuitive that the name of parameters don't matter.

The following shows an example of two overloaded method named `sum()`.

{% highlight java %}
public class OverloadSum {
    public static int sum(int a, int b) {
        return a + b;
    }
    
    public static int sum(int a, int b, int c) {
        return a + b + c;
    }
}
{% endhighlight %}

The methods have the same name, but the first version has 2 parameters and the second version has 3.

Return type of the methods does not matter. The following matrix shows this relationship, consider that we're overloading two methods (they have the same name).

<table style="text-align:center">
<tr>
<th>Same Paramethers</th>
<th>Same Return Type</th>
<th>Result</th>
</tr>
<tr>
<td>No</td>
<td>No</td>
<td>Compiling ok; overloaded methods</td>
</tr>
<tr>
<td>No</td>
<td>Yes</td>
<td>Compiling ok; overloaded methods</td>
</tr>
<tr>
<td>Yes</td>
<td>No</td>
<td>Compiling error: method already defined</td>
</tr>
<tr>
<td>Yes</td>
<td>Yes</td>
<td>Compiling error: method already defined</td>
</tr>
</table>

## Why Overloading

There are two reason for overloading a methods. The first is to support different data types. If you look at the <a href="http://docs.oracle.com/javase/7/docs/api/java/io/PrintStream.html#print(boolean)" target="_blank">`println()`</a> method of <a href="http://docs.oracle.com/javase/7/docs/api/java/io/PrintStream.html" target="_blank">`PrintStream`</a> class, which is used to output a line of text to the screen, you can see that there are different versions of the method, for different types. In this case, we can say the method is overloaded. The following shows a few overloaded version of `println()` from Java documentation.

- println(int x)
- println(float x)
- println(String x)

The second reason is to make some parameters of a method optional. For example, the following methods finds the minimum value of an array, but the second version has an additional second parameter that specify where the method should start looking. The implementation are omitted because they are not important.

{% highlight java %}
public class OverloadSum {
    public static int min(int[] a) { ... }
    
    public static int min(int[] a, int start) { ... }
}
{% endhighlight %}

## Overloading Constructors

This pattern is very popular in writing constructors. A class may have default values, and different versions of constructors take different numbers of parameters. Depending on the version called, the parameters that are not assigned get the default value.

The following shows an example of two version of constructor. When the first version of the constructor is called, a square will be created. The user has the option of calling the second version for a non-square. The main method is shown below the `Rectangle` class.

{% highlight java %}
public class Rectangle {
    int width;
    int height;

    public Rectangle(int w) {
        this(w, w);
    }

    public Rectangle(int w, int h) {
        this.width = w;
        this.height = h;
    }
}

public class Driver {
    public static void main(String[]) {
        Rectangle r1 = new Rectangle(10);     //Create a square
        Rectangle r2 = new Rectangle(10, 20); //Create a non-square
    }
}
{% endhighlight %}

Note that the first constructor actually calls the second constructor, using `this()`. However, calling another constructor has to be the first statement in a constructor.

## Static Methods

So can `static` method be overloaded? Static methods, like `main()` can be called without class instantiation. The answer is yes, `static` class can be overloaded, just as the first example above.

Of course, non-static methods can be overloaded as well.

The other question is can a non-static method overload a static method? The answer is, the code will compile just fine, but it's not really an overloading. The reason is that you can call the static version without instantiation, but you need an object for the non-static version. This is show below.

{% highlight java %}
public class Sum2 {
    public static int sum(int a, int b) {
        return a + b;
    }
    
    public int sum(int a, int b, int c) {
        return a + b + c;
    }
}

public class Driver {
    public static void main(String[]) {
        int s1 = Sum2.sum(1, 2);    //Calling static version
        Sum2 inst = new Sum2();
        int s2 = inst.sum(1, 2, 3); //Calling non-static version
    }
}
{% endhighlight %}