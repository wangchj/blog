---
layout: post
status: publish
published: true
title: Java Loops
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1232
wordpress_url: http://codenuggets.com/?p=1232
date: '2015-01-02 07:22:47 -0600'
date_gmt: '2015-01-02 07:22:47 -0600'
categories:
- Programming
- Java
tags:
- Java
- loops
- while
- do-while
- for
- for-each
- infinite loop
- iteration
- collections
- iterator
- nested loops
comments:
- id: 4140
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-05 05:52:24 -0600'
  date_gmt: '2015-01-05 05:52:24 -0600'
  content: "[&#8230;] Java Data and Data Types 2 Java Boolean Expressions Java Operator
    Precedence Java If and Else Java Loops Java Method Overloading Java [&#8230;]"
---
In the previous article, we covered `if` and `switch` statements that are used to selectively execute certain portion of our code based on certain conditions. In this article, we are going to cover another type of control construct called loops.

As the name implies, loops allow us to repeat certain portion of our code. Sometimes in programming, we need to do something over and over, depending on a condition. For example, we may ask the user of our program to enter a menu selection using the keyboard. If the user inputs an invalid selection, we'll need to ask the user again and again until a valid input is entered. Loop is another very fundamental construct in all programming languages.

In this article we are going to cover different types of loops. In fact all different loop constructs do the same; one kind of loop can be replaced with another kind of loop. There are situations where it is easier to use one kind of loop over the other; therefore Java has different loops as convenience. In this article we will cover, `while`, `do-while`, `for`, and `for-each` loops.

## The While Loop

The `while` loop continues while a condition is `true`. Consider the following snippet example, which outputs 1 to 10.

{% highlight java %}
int i = 1;
while (i <= 10) {
    System.out.println(i); //Print i
    i++;                   //Increment i by 1
} //End
{% endhighlight %}

```
Output:
1
2
3
4
5
6
7
8
9
10
```

<center><img src="/images/figures/java-loops/while.png" /></center>

The syntax is the same as an `if` statement: condition resides in parentheses and the body to execute are in braces, which are optional. If braces are omitted, only one line is allowed in the body.

## The Do-While Loop

The `do-while` has the similar structure as the `while` loop, but the looping condition is at the end of the loop, instead of at the beginning. This loop is useful when you want to execute the loop at least once. The conditional test is then executed after the first iteration.

{% highlight java %}
int i = 15;
do {
    System.out.println(i); //Print i
    i++;                   //Increment i by 1
} while (i <= 10); //End
{% endhighlight %}

```
Output:
15
```

<center><img src="/images/figures/java-loops/do-while.png" /></center>

Notice that although 15 is greater than 10, it is printed out because the condition is checked at the end of the loop. Also there must be a semicolon `;` at the end of the condition.

## The For Loop

The `for` loop is a concise way to write a loop because it places the **loop initialization**, the condition, and the step statement together. Consider the following example, which is functionally equivalent to the first example.

{% highlight java %}
for (int i = 1; i <= 10; i++) {
    System.out.println(i);
}
{% endhighlight %}

```
Output:
1
2
3
4
5
6
7
8
9
10
```

This code has the same out and flowchart as the first example. There are three parts in parentheses:

1. Initialization: this is the first part before the first semicolon (`int i = 1`).
2. The condition: this is the middle part (`i <=10`).
3. Step statement: this is the last part (`i++`).

Notice that these are the same parts that are present in previous loop forms, but it's less error prone because all parts are kept on the same line.

## The For-Each Loop

The `for-each` loop is another form of the `for` loop that was introduce in Java 1.5. It is use to iterate through collections that implement the <a href="http://codenuggets.com/2014/06/26/java-iterator/">Iterator</a> interface. Collections and iterators will be covered in later articles.

Consider the following example where we have an ArrayList collection that contains 5 elements. We can use the `for-each` loop to go through and print the entire collection.

{% highlight java %}
ArrayList<Integer> c = new ArrayList<Integer>();  //New ArrayList collection, c
c.add(1); c.add(2); c.add(3); c.add(4); c.add(5); //Add to collection, c

for (int i : c) {            //For each integer in c
    System.out.println(i);   //Print that element
}//End
{% endhighlight %}

```
Output:
1
2
3
4
5
```

<center><img src="/images/figures/java-loops/for-each.png" /></center>

## Nested Loops

We can put one loop inside another. This is called **nested loops**. Nested loops is useful technique and you will undoubtedly use in your program.

The following example shows a nested `for` loops.

{% highlight java %}
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= i; j++)
        System.out.print('*');
    System.out.println();
}
{% endhighlight %}

```
Output:
*
**
***
****
*****
```

In the code above, there are two control variables, `i` and `j`. The outer loop is controlled by `i`, whereas the inner loop is controlled by both `i` and `j`.

The outer loop repeat 5 times. In each iteration of the outer loop, the inner loop runs and prints out one row of `'*'`. After the inner loop ends a line break is printed and the control goes back to the outer loop.

Notice that the body of the inner loop only has one statement; therefore braces are not needed.

<center><img src="/images/figures/java-loops/nested-loop.png" /></center>

In theory, loops can be nested in infinitely many levels. For example, you can have a loop inside a loop that is inside another loop. However, one must be careful because every time you have a nested loop, the amount of work is multiplied, not added! Thoughtless nested loops of many levels could cause performance problems.

## Infinite Loop

All of the examples above have a clearly defined conditions for ranges we should loop. We could also define a loop that never ends. Consider the following example.

{% highlight java %}
int i = 1;
while (true) {
    System.out.println(i); //Print i
    i++;                   //Increment i by 1
} //End
{% endhighlight %}

This loop is very similar to the first example, except that the loop will never end and keeps print out integers, until the user manually ends the program or shuts down the computer.

Endless loops are useful in situations such as services or a loop that keeps polling user inputs. However in many situations, we should be careful with loop conditions. Sometimes we run into the situation that the program is no longer responding, it's very likely that our program has an unanticipated infinite loop.