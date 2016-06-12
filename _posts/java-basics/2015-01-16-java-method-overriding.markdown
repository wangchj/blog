---
layout: post
status: publish
published: true
title: Java Method Overriding
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1362
wordpress_url: http://codenuggets.com/?p=1362
date: '2015-01-16 00:00:44 -0600'
date_gmt: '2015-01-16 00:00:44 -0600'
categories:
- Programming
- Java
tags:
- Java
- override
- method overriding
- static
- final
- hiding
comments:
- id: 4183
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-01-16 00:01:41 -0600'
  date_gmt: '2015-01-16 00:01:41 -0600'
  content: "[&#8230;] Precedence Java If and Else Java Loops Java Method Overloading
    Java Constructor Java Inheritance Java Method Overriding Java [&#8230;]"
---
In the previous article, we covered class inheritance in Java, which is a feature to copy methods and member variables of another class into our class. We gave an example that since a square is a rectangle, the `Square` class can inherit the `Rectangle` class and get the `area()` for free.

But what happens when we inherit too much? The parent class we are inheriting from has a method that does not do what we want. In this case, we can override the behavior of such methods in our class. All we have to do to override a method is just provide our own definition of the method. Let's see how overriding works.

## Override a Method

The following program shows an example of method overriding. Class `Child` inherits class `Parent`, and overrides method `greet()`.

{% highlight java %}
class Parent {
    public void greet() {
        System.out.println("Hi this is the parent!");
    }
}

class Child {
    public void greet() {  //Overrides greet()
        System.out.println("Hi this is the child!");
        super.greet();
    }
}

class Driver {
    public static void main(String[] args) {
        Child child = new Child();
        child.greet();
    }
}
{% endhighlight %}

```
Output:
Hi this is the child!
Hi this is the parent!
```

Clearly, when overriding a method, the methods must have matching name and the parameter list.

Notice that although the child class overrides `greet()`, the parent's version is still accessible through the `super` reference.

## Static Method

Methods with the `static` modifier cannot be overriden. When a method with the same signature is present in the child class, it may appear that the method is overriden, but this is called **method hiding**.

Overriding and hiding are similar concepts. The difference is in scenarios of polymorphism. The following example shows the difference.

{% highlight java %}
class Parent {
    public static void classMethod() {
        System.out.println("Static method in Parent");
    }

    public void instanceMethod() {
        System.out.println("Instance method in Parent");
    }
}

class Child extends Parent {
    public static void classMethod() {
        System.out.println("Static method in Child");
    }

    public void instanceMethod() {
        System.out.println("Instance method in Child");
    }
}
 
class Driver {
    public static void main(String[] args) {
        Parent parent = new Child();
        parent.instanceMethod();
        parent.classMethod();
    }
}
{% endhighlight %}

```
Output:
Instance method of Child
Static method of Parent
```

## Final Method

Finally, non-static methods marked with `final` modifier cannot be overriden. When attempted, compiling error will occur.