---
layout: post
status: publish
published: true
title: Java Branching Statements
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1199
wordpress_url: http://codenuggets.com/?p=1199
date: '2015-01-01 02:02:12 -0600'
date_gmt: '2015-01-01 02:02:12 -0600'
categories:
- Programming
- Java
tags:
- Java
- control flow
- if-else
- program logic
- boolean expressions
- switch
comments:
- id: 4132
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-02 07:23:29 -0600'
  date_gmt: '2015-01-02 07:23:29 -0600'
  content: "[&#8230;] Classes and Objects Java Arithmetic Operators Java Data and
    Data Types 2 Java Boolean Expressions Java If and Else Java Loops Java [&#8230;]"
---
In the previous article, we covered boolean expressions, which have a value of `true` or `false`, and logical operators that work on boolean values. This article covers how to use boolean expressions (or conditions) to decide what portion of our program to execute. For example, if a certain condition is true, our program should do this; otherwise is should do something else.

Flow control statements are the most fundamental concepts of programming and is essential in all programming languages. These statements allow us to add logic and intelligence in our program. In this article, we cover flow branching using `if-else` and `switch` constructs.

## `if` Statement

The `if` statement allows us to execute a portion of our program only when a condition is true. Consider the following snippet, and the flowchart that follows.

{% highlight java %}
System.out.println("Hello!");

if (friday) {
    System.out.println("Happy Friday!");
}

System.out.println("Goodbye");
{% endhighlight %}

<center><img src="http://codenuggets.com/wp-content/figures/java-if-else/if.png" /></center>

Line 3 is the start of the `if` statement, which contains a very simple condition, `friday`. The condition must be enclosed in parentheses. The condition can be a very complex boolean expression or can simply be a boolean variable, as in this case. Spaces are generally not important in Java and can be added or removed to prettify the code.

The body of the `if` statement, which prints out `"Happy Friday"`, is enclosed in braces, `{}`. The braces are optional and if omitted only the next statement is considered the body. No doubt as you have already already figured out, the body is only executed when the variable `friday` is true.

## If-Else Statement

We can add a `else` section to the `if` statement to specify what to do if the condition is `false`. Consider the following snippet example.

{% highlight java %}
System.out.println("Hello!");

if (friday) {
    System.out.println("Happy Friday!");
}
else {
    System.out.println("Have a good day!");
}

System.out.println("Goodbye");
{% endhighlight %}

<center><img src="http://codenuggets.com/wp-content/figures/java-if-else/if-else.png" /></center>

If the condition `friday` is `true`, then the program prints out `"Happy Friday!"`; otherwise it prints out `"Have a goody day!"`. Once again the braces is optional for the `else` section. If omitted, only one line is consider the body.

## Neted If and Else-If

We can have `if` statements inside an `if` statement. This is called **nested if statements**. Let's change our example a little and say we have a variable called `weekday` and 1 = Monday, 2 = Tuesday, and so on. Consider the following example.

{% highlight java %}
if (weekday == 1) {
    System.out.println("Happy Monday!");
}
else {
    if (weekday == 2) {
        System.out.println("Happy Tuesday!");
    }
    else {
        if (weekday == 3) {
            // ...
        }
    }
}
{% endhighlight %}

<center><img src="http://codenuggets.com/wp-content/figures/java-if-else/nested-if.png" /></center>

We can make the above code easier to read using `else if`. The following code is equivalent to the code above.

{% highlight java %}
if (weekday == 1) {
    System.out.println("Happy Monday!");
}
else if (weekday == 2) {
    System.out.println("Happy Tuesday!");
}
else if (weekday == 3) {
    // ...
}
// ...
{% endhighlight %}

## Swtich Statement

In the previous example, we have several cases for the `weekday` variable, and one `if` or `else if` block for each case. This kind of code branching that is based on selection of a value is perfect for `switch` statements. We can rewrite the previous as follows.

{% highlight java %}
switch (weekday) {
    case 1:
        System.out.println("Happy Monday!");
        break;
    case 2:
        System.out.println("Happy Tuesday!");
        break;
    case 3:
        System.out.println("Happy Wednesday!");
        break;
    
    // case ...

    default:
        System.out.println("Hey weekday is not a valid value!");
} //end of switch
// Goodbye
{% endhighlight %}

This code is equivalent to the previous code that uses `else if`, but it is a bit more concise and readable. At the end of each case, a `break` statement must be provided to jump to the end of the branching to Goodbye. If `break` is not provided, the code will continue to the next case.

If the selection value does not match any of the cases, the `default` case will be executed. In our case, we just print out the value is not valid!