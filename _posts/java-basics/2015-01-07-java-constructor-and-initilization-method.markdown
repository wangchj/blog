---
layout: post
status: publish
published: true
title: Java Constructor and Initilization Method
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1288
wordpress_url: http://codenuggets.com/?p=1288
date: '2015-01-07 18:00:13 -0600'
date_gmt: '2015-01-07 18:00:13 -0600'
categories:
- Programming
- Java
tags:
- constructor
- singleton
- factory method
comments:
- id: 4168
  author: Java Inheritance | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2015/01/13/java-inheritance/
  date: '2015-01-13 06:22:53 -0600'
  date_gmt: '2015-01-13 06:22:53 -0600'
  content: "[&#8230;] Previous PostJava Constructor and Initilization Method [&#8230;]"
- id: 4177
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-14 17:33:18 -0600'
  date_gmt: '2015-01-14 17:33:18 -0600'
  content: "[&#8230;] Boolean Expressions Java Operator Precedence Java If and Else
    Java Loops Java Method Overloading Java Constructor Java Inheritance Java [&#8230;]"
---
In our earlier article <a href="http://codenuggets.com/2014/11/07/java-classes-and-objects/">Classes and Objects</a>, we showed how to write a constructor for a simple class. In this article, we are going to dive deeper into the topic and show how constructors work and consider different types of constructors. 

## Writing Constructors

A constructor is a special method, in a class, called by our program when a new object is instantiated. The purpose is to set the new object to a known state to be used in our program. A constructor has the same name as the class and no return type. The constructor is implicitly called by Java, and cannot be called again once the object is constructed. The result (what is returned) is a reference to the new object. Consider the following example.

{% highlight java %}
public class Rectangle {
    int width;
    int height;

    public Rectangle(int w) {
        this(w, w);
    }

    public Rectangle(int w, int h) {
        width = w;
        height = h;
    }
}

public class Driver {
    public static void main(String[] args) {
        Rectangle rec1 = new Rectangle(10);    //Calls first constructor
        Rectangle rec2 = new Rectangle(5, 10); //Calls second constructor
    }
}
{% endhighlight %}

In the example above, the `Rectangle` class has two constructors; this is called **overloaded constructor**. The first version has one integer parameter (`int w`) and makes a square rectangle. The second version takes two parameters (`int w, int h`) and lets the programmer sets the both the width and width of the rectangle.

Notice that the first constructor actually calls the second constructor using the `this()` reference, which refers to the current object. This is a common pattern you see in Java where a more general version of a method calls a more specific version.

The example above also provides a `Driver` class. The class constructor creates two instances of the `Rectangle` class. **Notice** that constructors have to be invoked using the `**new**` operator.

The first rectangle is constructed using the first constructor, which in terms calls the second constructor. The second rectangle is constructed using the second. The result of the calls are stored in the reference variable `rec1`, and `rec2`.

## Parameter-Less Constructor

A constructor does not necessarily have parameters. Many constructors just sets the members variable to default values so there is no need for parameters. The following example shows a parameter-less constructor for the `Rectangle` class.

{% highlight java %}
public class Rectangle {
    int width;
    int height;

    public Rectangle() {
        width = 10;
        height = 10;
    }
}

public class Driver {
    public static void main(String[] args) {
        Rectangle rec1 = new Rectangle();    //Calls parameter-less constructor
    }
}
{% endhighlight %}

The constructor just defaults the rectangle to 10 x 10, and the programmer can modify these later. Note that it is a good idea to provide a specific version of constructor when possible, so the person who uses your class can simply initialize the object in one step.

## Default Constructor

If you do not write a constructor for you class, Java will provide a default parameter-less constructor for you, so that you can still construct your class. The default constructor just sets all variables to default values. As described in the first article about data types, the following are the default values.

<table style="text-align:center">
<tr>
<th>Type</th>
<th>Default Value</th>
</tr>
<tr>
<td>Numerics</td>
<td>0</td>
</tr>
<tr>
<td>Boolean</td>
<td>`false`</td>
</tr>
<tr>
<td>References</td>
<td>`null`</td>
</tr>
</table>
The default constructor is not available for classes that have constructors. The following example produce a compiling error, because the default constructor is not available, and the driver class must use one of the provided.

{% highlight java %}
public class Rectangle {
    int width, height;

    public Rectangle(int w) { ... }
}

public class Driver {
    public static void main(String[] args) {
        Rectangle rec1 = new Rectangle();    //Compiling error
    }
}
{% endhighlight %}

## Initialization Method

Constructors not only can call other constructors, but can also call other methods in the class. This is useful when we want to share code in our constructors. In this case, we can put this code in a separate method and called by our constructors.

A constructor can only call another constructor on the first line. To have a initialization method is particularly useful to have code shared among constructors that can be called anywhere inside these constructors.

Consider the following two examples, where the first is illegal, while the second is legal.

{% highlight java %}
public class Rectangle {
    int width, height;

    public Rectangle(int w) {
        int h = w * 2;
        this(w, h);     //Illegal; constructor has to be call first thing
    }

    public Rectangle(int w, int h) {
        width = w; height = h;
    }    
}
{% endhighlight %}

The following is legal.

{% highlight java %}
public class Rectangle {
    int width, height;

    public Rectangle(int w) {
        int h = w * 2;
        init(w, h);     //Legal
    }

    public Rectangle(int w, int h) {
        init(w, h);
    }

    public void init(int w, int h) {
        width = w; height = h;
    }
}
{% endhighlight %}

## Private Constructors

Constructor can be private. When the only constructor is private in a class, the class cannot be instantiated using the `new` operator. This is often used in <a href="http://en.wikipedia.org/wiki/Singleton_pattern" target="_blank">singleton</a> pattern, where the writer of the class does not want other programmers to create instances of the class. Instead, an instance should be obtain through a factory method of the class.

Consider the following example.

{% highlight java %}
public class Rectangle {
    int width, height;
    Rectangle instance = new Rectangle(10, 20);

    private Rectangle(int w, int h) {
        width = w, height = h;
    }

    public getInstance() {
        return instance;
    }
}
{% endhighlight %}

In the example above, only a single instance of this class is ever created. When a user wants an instance, they have to call the factory method, `getInstance()`.