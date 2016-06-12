---
layout: post
status: publish
published: true
title: Java Abstract Class
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1398
wordpress_url: http://codenuggets.com/?p=1398
date: '2015-01-20 04:36:20 -0600'
date_gmt: '2015-01-20 04:36:20 -0600'
categories:
- Programming
- Java
tags:
- Java
- inheritance
- abstract
- abstract class
- abstract method
- final class
comments:
- id: 4209
  author: Java Interface | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/06/20/java-interface/
  date: '2015-01-21 23:15:47 -0600'
  date_gmt: '2015-01-21 23:15:47 -0600'
  content: "[&#8230;] time, we covered abstract classes. In this article, we are going
    to cover a similar concept called interface (not the same as a [&#8230;]"
- id: 4227
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-28 23:28:02 -0600'
  date_gmt: '2015-01-28 23:28:02 -0600'
  content: "[&#8230;] Java Method Overloading Java Constructor Java Inheritance Java
    Method Overriding Java Polymorphism Java Abstract Class Java Interface Java [&#8230;]"
---
In our previous article about <a href="http://codenuggets.com/2015/01/18/java-polymorphism/">polymorphism</a>, we gave an example of a `Shape` class inherited by three subclasses, `Rectangle`, `Triangle`, and `Circle`. With polymorphism, a variable of type `Shape` can reference an object of any of the 3 subclasses.

However if you look at the example closely, the `area()` method of the `Shape` class (shown below) actually returns 0, because shape is a very abstract concept, and we can't actually compute the area, so we just wrote a placeholder method.

{% highlight java %}
class Shape {
    public double area() {
        return 0;
    }
}
{% endhighlight %}

This is where the idea of abstract class comes in. An **abstract class** in Java is a class that cannot be instantiated, but allows programmer to define methods for subclasses. Let's see how this works.

## Defining Abstract Class

An abstract class is marked with the `abstract` modifier, as shown below.

{% highlight java %}
abstract class Shape {
    public abstract double area();
}
{% endhighlight %}

Abstract classes usually contain abstract method, like `area()` above, because that is the purpose of an abstract class.

Also an `abstract` class cannot be a `final` class. The reason is that a `final` class cannot be inherited, but an `abstract` has to be inherited or else it cannot be instantiated and useless.

## Extending Abstract Class

A subclass of an abstract class must override all of the parent's abstract methods, or it must be declared abstract. For example, the `ColorShape` class must be abstract because it does not override the `area()` method.

{% highlight java %}
abstract class ColorShape extends Shape {
    protected String color;
    public String getColor() {
        return color;
    }
}
{% endhighlight %}

## Polymorphism with Abstract Class

Abstract classes go hand-in-hand with polymorphism. As shown the previous example, we can define a very high-level concept as an abstract class, with abstract methods. We let the concrete subclasses to write the logic for these methods.

The good thing about this approach is that we do not accidentally execute some placeholder method, and Java will pick the correct method to execute based on the concrete object type.