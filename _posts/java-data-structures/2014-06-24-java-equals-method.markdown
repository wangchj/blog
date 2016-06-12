---
layout: post
status: publish
published: true
title: Java equals Method
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 902
wordpress_url: http://codenuggets.com/?p=902
date: '2014-06-24 18:02:45 -0500'
date_gmt: '2014-06-24 18:02:45 -0500'
categories:
- Programming
- Java
tags:
- equals
- equality
comments:
- id: 3087
  author: Java Comparable Interface | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/06/29/java-comparable-interface/
  date: '2014-06-29 03:43:35 -0500'
  date_gmt: '2014-06-29 03:43:35 -0500'
  content: "[&#8230;] the previous article, we see how we can define equality in our
    class and compare two objects using the equals() method. [&#8230;]"
- id: 3907
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2014-11-07 23:51:04 -0600'
  date_gmt: '2014-11-07 23:51:04 -0600'
  content: "[&#8230;] Java equals Method Java Comparable Interface Java Comparator
    Interface Java Iterator Setup JUnit in jGrasp [&#8230;]"
- id: 4121
  author: Java Boolean Expressions | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/12/27/java-boolean-expressions/
  date: '2014-12-29 01:47:07 -0600'
  date_gmt: '2014-12-29 01:47:07 -0600'
  content: "[&#8230;] memory, regardless of object&#8217;s content. For this reason,
    objects are usually compared using equals() method, or using implementation of
    Comparable and Comparator [&#8230;]"
---
Every class in Java has an [`equals()`](http://docs.oracle.com/javase/7/docs/api/java/lang/Object.html#equals(java.lang.Object)) method inherited from the `Object` class. Newcomers to Java may be asking what is the purpose of this method? As a side note, C# has the similar method. The `equals()` method is used to compare two objects (usually of same class). If the objects are logically the same, then the method returns `true`, else `false`.

## Determining Equality

What do we mean two objects are logically equal? This means that, they may not be the same object in memory, but they contain the same data. Take the following code for example. The program creates two different instances of `Book` in memory, but they have same title and author, so logically they are the same.

{% highlight java %}
public class EqualsExample {
    public static void main(String[] args) {
        //Title, author, page count
        Book book1 = new Book("Angels and Demons", "Dan Brown", 300);
        Book book2 = new Book("Angels and Demons", "Dan Brown", 400);
        boolean same = book1.equals(book2); //Should return true
    }
}
{% endhighlight %}

The next question is what determines two objects are the same? This is determined by whoever wrote the class. Using the code above for example, if the author of the `Book` class determines that only the **title** and **author** matters in determining equality, then `book1.equals(book2)=>true`. However, if the number of pages should also be taken into consideration, then `book1.equals(book2)=>false`. Therefore, equality is determined by the context in which the code is written.

## Equality Operator

The equality operator `==` is often used in comparison, why can't we use it to compare two objects? The answer is that `==` is used to compare <a href="http://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html" target="_blank">primitive types</a>. For <a href="http://docstore.mik.ua/orelly/java-ent/jnut/ch02_10.htm" target="_blank">reference types</a>, `==` is used to determine if two variables holds the same reference (address) to the same object in memory (this is called alias checking). However, often objects are not the same in memory, but are logically equivalent, as shown in example above.

Another reason is that there are so many ways to define equality of two objects. In the example above using the `Book` class, we can define two books are equal if the titles are equal, or both title and author have to be equal, or even, they have to be the same object to be equal. Using `equals()` method provides the flexibility to the coder to decide what it means to be equal.

Another note is that, if a class does not override the `equals()`, then the version inherited from the `Object` class only does alias checking.

## Recipe

The following is a good recipe for writing `equals()` method. Remember, what we are doing here is actually overriding the method provided by the `Object` class, so method signature must match what is defined by the class. This recipe is obtained from Dr. Dean Hendrix of Auburn University.

{% highlight java %}
public class Book {
    private String title;
    private String author;
    private int    pages;

    public boolean equals(Object obj) { //Must be of type Object
        if(obj == this) return true; //Check for aliasing
        if(obj == null) return false; //Check for null
        if(!(obj instanceof Book)) return false; //Check for type compatibility
        Book that = (Book)obj;
        return this.title.equals(that.title) && //Check all significant fields
               this.author.equals(that.author);
    }
}
{% endhighlight %}

Note that the parameter (Object obj) must be of type `Object`, because we are overriding the method.