---
layout: post
status: publish
published: true
title: Java Inheritance
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1302
wordpress_url: http://codenuggets.com/?p=1302
date: '2015-01-13 06:22:48 -0600'
date_gmt: '2015-01-13 06:22:48 -0600'
categories:
- Programming
- Java
tags:
- Java
- inheritance
- class hierarchy
- OOP
- constructors
comments:
- id: 4179
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-15 06:39:03 -0600'
  date_gmt: '2015-01-15 06:39:03 -0600'
  content: "[&#8230;] Java Operator Precedence Java If and Else Java Loops Java Method
    Overloading Java Constructor Java Inheritance Java [&#8230;]"
- id: 4242
  author: Java Generics | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2015/02/02/java-generics/
  date: '2015-02-02 20:13:46 -0600'
  date_gmt: '2015-02-02 20:13:46 -0600'
  content: "[&#8230;] collections use the most general data type, the Object class.
    As we mentioned in the article Java Inheritance, every class inherits from the
    Object class, so any type can be stored in these collections that [&#8230;]"
---
In this article, we are going to cover one famous feature of Java, that is inheritance. If you ask someone, what is OOP? They will no doubt say something about inheritance and class hierarchy. Of course, this is just one feature of object-oriented concepts, but it's an important one. We're going to find out what it is!

## What is Inheritance?

Inheritance is a code reuse technique in which one class inherits, or copies, methods and member variables of another class. As an example, consider that we have two classes `Rectangle` and `Square` as shown in the figure below. The `Rectangle` class has two `protected` member variables `width` and `height`, one `public` method `area()` that computes the area, and one `private` method `sum()`.

Conceptually a square is a rectangle, and the logic to compute the area is the same. In this case, it make sense for the `Square` class to inherit the `Rectangle` class and reuse the `area()` method. The figure below shows the inheritance relationship, which denoted by <img src="/images/figures/java-inheritance/arrow.png" /> arrow.

<center><img src="/images/figures/java-inheritance/inherit-basic.png" /></center>

In Java, inheritance is done using the `**extends**` keyword, as shown in the code below.

{% highlight java %}
public class Rectangle {
    protected int width, height;

    public Rectangle(int width, int height) {
        this.width  = width;
        this.height = height;
    }

    public int area() {
        return width * height;
    }
}

public class Square extends Rectangle {
    public Square(int width) {
        super(width, width);
    }
}

public class Driver {
    public static void main(String[] args) {
        Square s = new Square(10);
        System.out.println(s.area());  //Prints out 100
    }
}
{% endhighlight %}

```
Output:
100
```

In the code above, `Square` (the child class), extends the `Rectange` (the parent or super class); so the `Square` gets the `width`, `height`, and `area()` method without any code. Note that the `Driver` class is able to call the `area()` method of the `Square` object.

## What is Inherited

Java allows what is inherited by a child class, based on the visibility modifiers. The following table summarizes what is inherited based on modifier.

<table style="text-align:center">
<tr>
<th>Visibility</th>
<th>Inherited by Child</th>
<th>Accessible by Another Class</th>
</tr>
<tr>
<td></td>
<td>Class of same package</td>
<td>Class of same Package</td>
</tr>
<tr>
<td>public</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<td>protected</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr>
<td>private</td>
<td>No</td>
<td>No</td>
</tr>
</table>
As one can see, public and protected members are inherited by child class; whereas private members are not not.

In addition, `static` and `final` methods are also inherited, when visibility allows.

<table style="text-align:center">
<tr>
<th>Modifier</th>
<th>Inherited by Child</th>
</tr>
<tr>
<td>static</td>
<td>Yes</td>
</tr>
<tr>
<td>final</td>
<td>Yes</td>
</tr>
</table>
The following example shows inheritance of a `static final` method.

{% highlight java %}
public class Rectangle {
    public final static int area(int w, int h) {
        return w * h;
    }
}

public class Square extends Rectangle {}

public class Driver {
    public static void main(String[] args) {
        System.out.println(Square.area(10, 20));  //Prints out 200
    }
}
{% endhighlight %}

```
Output:
200
```

## Inherited Constructors

As one can imagine, public and protected constructors are also inherited. However, they are not available when constructing the child class. For example, the following code will produce compiling error.

{% highlight java %}
public class Driver {
   public static void main(String[] args) {
        Square s = new Square(10, 10);
    }
}
{% endhighlight %}

Although, the constructor of the `Rectangle` class is public and in theory inherited by the `Square` class, it cannot be used when instantiating the `Square` class. The reason for this is that, constructors have the same name as the class. When we invoke `new Square()`, we are instructing Java to look for a method named `Square()`, which excludes the `Rectangle` constructor, named `Rectangle()`.

Nonetheless, child class is able to access constructors of parent class. As shown in the first code example, parent constructors can be called using `**super()**`, which is a reference to the parent class in Java. As expected, based on the parameters provided, Java will call the correct constructor.

One thing to note is that, if used, `super()` has to be the first statement in the child constructor. If the constructor needs to do something before calling the parent's constructor, consider using <a href="http://codenuggets.com/2015/01/07/java-constructor-and-initilization-method/">initialization methods</a>.

## The Object Class

The `Object` class is the root of Java's class hierarchy. Every class in Java is a descendant of the `Object` class and inherit from it. If a class does not explicitly inherit a class using `extends`, then it is a direct child of the `Object` class. In other words, every class in Java has a parent, except for the `Object` class.

The `Object` class defines the most generic skeleton methods that make Java work. For a list of methods defined by this class, see <a href="http://docs.oracle.com/javase/7/docs/api/java/lang/Object.html" target="_blank">Object</a> API.

## Uninheritable Class

A class that is marked with the `final` modifier cannot be inherited. The following example produces a compiling error, because class `NoExtend` has `final` modifier.

{% highlight java %}
final class NoExtend {}

class Child extends NoExtend {}  //Compiling Error: cannot inherit from final NoExtend
{% endhighlight %}

## Java Class Hierarchy and Class Library

The Java class library is a large hierarchy of classes that can be used by programmers. The root of this hierarchy of course is the `Object` class. For example, the following figure shows just a few classes in this hierarchy.

<center><img src="http://www.webbasedprogramming.com/Developing-Professional-Java-Applets/f4-6.gif" /></center>

Programmers can add to this hierarchy by writing classes that extending classes in the hierarchy.