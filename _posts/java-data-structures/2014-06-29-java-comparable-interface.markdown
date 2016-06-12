---
layout: post
status: publish
published: true
title: Java Comparable Interface
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 920
wordpress_url: http://codenuggets.com/?p=920
date: '2014-06-29 03:24:01 -0500'
date_gmt: '2014-06-29 03:24:01 -0500'
categories:
- Programming
- Java
tags: []
comments:
- id: 3088
  author: Java Comparator | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/06/29/java-comparator/
  date: '2014-06-29 19:02:15 -0500'
  date_gmt: '2014-06-29 19:02:15 -0500'
  content: "[&#8230;] the relationship of the two objects based on the following return
    values (which are the same as the compareTo() [&#8230;]"
- id: 4138
  author: Java Boolean Expressions | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/12/27/java-boolean-expressions/
  date: '2015-01-05 03:38:02 -0600'
  date_gmt: '2015-01-05 03:38:02 -0600'
  content: "[&#8230;] For this reason, objects are usually compared using equals()
    method, or using implementation of Comparable and Comparator [&#8230;]"
- id: 4202
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-20 04:37:33 -0600'
  date_gmt: '2015-01-20 04:37:33 -0600'
  content: "[&#8230;] equals Method Java Comparable Interface Java Comparator Interface
    Java Iterator Setup JUnit in [&#8230;]"
---
In the <a href="http://codenuggets.com/2014/06/24/java-equals-method/" target="_blank">previous article</a>, we see how we can define equality in our class and compare two objects using the `equals()` method. In this article, we are going to define additional <em>less than</em> and <em>greater than</em> relations in our class using the [`Comparable<T>`](http://docs.oracle.com/javase/7/docs/api/java/lang/Comparable.html) interface.

The [`Comparable<T>`](http://docs.oracle.com/javase/7/docs/api/java/lang/Comparable.html) interface defines relative order in our class, which is useful for sorting. For example, let's say we're working on a program that keeps a list of books in sorted order by book title. In order to keep the list sorted, we need to know more than just if two books are equal. What we need is which book should come before the other.

## Comparable Interface

The goals of `Comparable` is to compare two objects and see if one is less than, greater than, or equal to the other. The interface only has 1 method, `compareTo()`, which takes an object as parameter. For objects `a` and `b` that implements `Comprable`, `a.compareTo(b)` returns:

1. Negative integer: if `a` < `b`
2. Positive integer: if `a` > `b`
3. 0: if `a` = `b`

Note, `a` < `b` means `a` is logically less than `b`, depends on how `compareTo()` is implemented.

## Example

The following snippet shows an example `Person` class that defines the ordering based only on the person's age.

{% highlight java %}
class Person implements Comparable<Person> {
    private String Name;
    private String Gender;
    private int    age;

    /** This method is required by Comparable interface */
    public compareTo(Person that) {
        if(this.age == that.age) return 0;
        else if(this.age < that.age)  return -1;
        else return 1;
    }
}
{% endhighlight %}

The following code creates an array of 3 `Person` objects and sorts the array using Java's sorting method.

{% highlight java %}
class Demo {
    public static void main(String[] args)
    {
        Person[] a = new Person[3]; //Create an array of Person
        a[0] = new Person("John", "M", 40); //Create Person Objects
        a[1] = new Person("Anne", "F", 20);
        a[2] = new Person("Bill", "M", 50);
        Arrays.sort(a); //Sort the array

        //After the sort, a becomes
        //a[0] = {"Anne", "F", 20}
        //a[1] = {"John", "M", 40}
        //a[2] = {"Bill", "M", 50}
    }
}
{% endhighlight %}

<!--<br />
The `Comparable<T>` interface defines only the `compareTo()` method. The goal of this method is to compare<br />
-->

## When to Implement

When should the `Comparable` interface be used? It makes sense for a numeric data type to implement this interface since, numeric values usually have a natural ordering. More generally, whenever your class has an natural ordering, it is a good idea to implement this interface, so that objects of your classes can be sorted by Java's sorting algorithms.

`Comparable` is also implemented by many of build-in types and wrapper classes, so that they can be sorted in collections. A few examples of these classes include: <a href="http://docs.oracle.com/javase/7/docs/api/java/lang/Integer.html" target="_blank">Integer</a>, <a href="http://docs.oracle.com/javase/7/docs/api/java/lang/Double.html" target="_blank">Double</a>, and <a href="http://docs.oracle.com/javase/7/docs/api/java/lang/String.html" target="_blank">String</a>.