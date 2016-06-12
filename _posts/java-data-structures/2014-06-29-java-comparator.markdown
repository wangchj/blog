---
layout: post
status: publish
published: true
title: Java Comparator Interface
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 956
wordpress_url: http://codenuggets.com/?p=956
date: '2014-06-29 17:51:06 -0500'
date_gmt: '2014-06-29 17:51:06 -0500'
categories:
- Programming
- Java
tags: []
comments:
- id: 4129
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-01 02:06:25 -0600'
  date_gmt: '2015-01-01 02:06:25 -0600'
  content: "[&#8230;] equals Method Java Comparable Interface Java Comparator Interface
    Java Iterator Setup JUnit in [&#8230;]"
- id: 4137
  author: Java Boolean Expressions | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/12/27/java-boolean-expressions/
  date: '2015-01-05 03:34:41 -0600'
  date_gmt: '2015-01-05 03:34:41 -0600'
  content: "[&#8230;] objects are usually compared using equals() method, or using
    implementation of Comparable and Comparator [&#8230;]"
- id: 4241
  author: COMP2210 A2 | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2015/02/02/comp2210-a2/
  date: '2015-02-02 17:48:52 -0600'
  date_gmt: '2015-02-02 17:48:52 -0600'
  content: "[&#8230;] parameter comp is an instance of a Comparator class. As noted
    previously, the Comparator determines which element is greater than or less than
    the [&#8230;]"
---
In addition to using the `Comparable` interface, there is another standard interface we can use to compare objects for equality, and inequalities (greater than, or less than): using the `Comparator` interface.

## Interface

The `Comparator<T>` interface defines only one method, `compare(T a, T b)`. The method takes 2 objects, `a` and `b` and determines the relationship of the two objects based on the following return values (which are the same as the `<a href="http://codenuggets.com/2014/06/29/java-comparable-interface/" target="_blank">compareTo()</a>` method):

1. Negative integer: if `a` < `b`
2. Positive integer: if `a` > `b`
3. 0: if `a` = `b`

## Comparator Comparable Comparison

So what is the difference between Comparable interface and Comparator interface? The `Comparable` defines these relationship inside the class of the objects being compared; therefore, `compareTo()` method only takes one parameter. In contrast `Comparator` is implemented in a separate class. From the interface above, we can see the `compare()` method of Comparator interface takes two parameters.

As we mentioned earlier, there are many ways to define order on objects. Take the `Person` class that follow for example, we can sort the class based on any of its attributes, such as name or age. When we use Comparable interface, there is only one way to compare objects. With Comparator we can write multiple classes that implement the interface and have different ways to compare `Person` object based on situation. The follow code shows this.

{% highlight java %}
class Person {
    public String name;
    public String gender;
    public int    age;
    //Other members and methods
}

/** Comparator to compare by name */
class PersonByName implements Comparator<Person> {
    public int compare(Person a, Person b) { return a.name.compareTo(b.name); }
}

/** Comparator to compare by age */
class PersonByAge implements Comparator<Person> {
    public int compare(Person a, Person b) {
        if(a.age == b.age) return 0;
        else if(a.age < b.age)  return -1;
        else return 1;
    }
}
{% endhighlight %}

## Sorting using Comparator

The flexibility of Comparator allow us to sort objects of a class in different ways (e.g. by name, or by age). Sorting methods in both `<a href="http://docs.oracle.com/javase/7/docs/api/java/util/Arrays.html" target="_blank">Arrays</a>` and `<a href="http://docs.oracle.com/javase/7/docs/api/java/util/Collections.html" target="_blank">Collections</a>` class take an additional `Comparator` object. The following code first sorts the array of `Person` first by name, then by age.

{% highlight java %}
class Demo {
    public static void main(String[] args) {
        Person[] a = new Person[3]; //Create an array of Person
        a[0] = new Person("John", "M", 40); //Create Person Objects
        a[1] = new Person("Anne", "F", 20);
        a[2] = new Person("Bill", "M", 50);
        Arrays.sort(a, new PersonByName()); //Sort the array by name
        Arrays.sort(a, new PersonByAge()); //Sort the array by age
    }
}
{% endhighlight %}