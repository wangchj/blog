---
layout: post
status: publish
published: true
title: Java Polymorphism
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1379
wordpress_url: http://codenuggets.com/?p=1379
date: '2015-01-18 03:43:40 -0600'
date_gmt: '2015-01-18 03:43:40 -0600'
categories:
- Programming
- Java
tags:
- Java
- polymorphism
- polymorphic
- type
- area
- triangle
- Heron's Formula
comments:
- id: 4193
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-18 03:48:48 -0600'
  date_gmt: '2015-01-18 03:48:48 -0600'
  content: "[&#8230;] Else Java Loops Java Method Overloading Java Constructor Java
    Inheritance Java Method Overriding Java Polymorphism Java [&#8230;]"
- id: 4201
  author: Java Abstract Class | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2015/01/20/java-abstract-class/
  date: '2015-01-20 04:36:26 -0600'
  date_gmt: '2015-01-20 04:36:26 -0600'
  content: "[&#8230;] our previous article about polymorphism, we gave an example
    of a Shape class inherited by three subclasses, Rectangle, Triangle, and [&#8230;]"
- id: 4210
  author: Java Interface | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/06/20/java-interface/
  date: '2015-01-21 23:23:06 -0600'
  date_gmt: '2015-01-21 23:23:06 -0600'
  content: "[&#8230;] we can do polymorphism using interfaces. What this mean is that
    we can create a variable of an interface, and assignment [&#8230;]"
---
Previously, we said that inheritance is a feature of Java (and many object-oriented languages) that allows us to inherit variables and methods from another class. Inheritance denotes an "is a" relationship between classes. For example, if class `Square` inherits class `Rectangle`, then technically, an object of `Square` <em>is an</em> object of `Rectangle` because both classes have the same methods we can call.

In this article we are going to cover polymorphism in Java, which is another well known concept of object-oriented programming and it is very much related to inheritance. The word polymorphism may sound scary, but the idea is actually really simple. **Polymorphism**, meaning "many forms", simply means a variable can be assigned an object of child classes (or sub-types) because of the "is a" relationship. Let's see how this works in Java.

## Simple Class Hierarchy

Let's say we have the following very simple hierarchy of classes of shapes.

<center><img src="http://codenuggets.com/wp-content/figures/java-polymorphism/polyshapes.png" /></center>

The `Shape` class is the parent of `Rectangle`, `Triangle`, and `Circle`. The figure can be translated to the following Java classes.

{% highlight java %}
class Shape {
    public double area() {
        return 0;
    }
}
{% endhighlight %}

{% highlight java %}
class Rectangle extends Shape {
    protected int width, height;

    public Rectangle(int width, int height) {
        this.width = width; this.height = height;
    }

    public double area() {
        return width * height;
    }
}
{% endhighlight %}

{% highlight java %}
class Triangle extends Shape {
    protected int a, b, c;

    public Triangle(int a, int b, int c) {
        this.a = a; this.b = b; this.c = c; //Assume lengths a, b, c are valid
    }

    public double area() {
        double s = (a + b + c) / 2;
        return Math.sqrt(s * (s - a) * (s - b) * (s - c));
    }
}
{% endhighlight %}

{% highlight java %}
class Circle extends Shape {
    protected int r;

    public Circle(int r) {
        this.r = r;
    }

    public double area() {
        return Math.PI * r * r;
    }
}
{% endhighlight %}

The following program contains an array of shape objects of different type. The array itself is the type `Shape`, but it contains object of other classes. In this case, we call this array **polymorphic**.

{% highlight java %}
class Program {
    public static void main(String[] args) {
        Shape[] a = {  //Polymorphic array of shapes
            new Shape();
            new Rectangle(1, 10),
            new Triangle(3, 4, 5),
            new Circle(5)
        };

        for(Shape s : a)
            System.out.println("The area of " + s.getClass().getName() +
                " is " + s.area());
}
{% endhighlight %}

```
Output:
The area of Shape is 0.0
The area of Rectangle is 10.0
The area of Triangle is 6.0
The area of Circle is 78.54
```

From the code above, we can see that we can get the actual type and name of the shape using the `getClass()` method. We can also check if an object is an instance of a class using the `instanceof` operator.

## Benefit of Polymorphism

I hope you can see from the previous example some benefits of using polymorphic technique. Ultimately, the purpose of polymorphism is to make our code more generic. As shown in the example above, we only have one `for` loop to output the area, without using any `if` statements to consider each shape separately.

In the Java API, you will often see methods with parameters of very generic type. This allows programmers to pass in different implementations of an algorithm to get a different behavior in the program with the same code to suit the specific need. One such example is the `equals` of the `Object` class, which takes an object of type `Object`.