---
layout: post
status: publish
published: true
title: Java Generics
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1433
wordpress_url: http://codenuggets.com/?p=1433
date: '2015-02-02 20:13:38 -0600'
date_gmt: '2015-02-02 20:13:38 -0600'
categories:
- Programming
- Java
tags:
- Java
- generics
- generic type
- generic method
comments:
- id: 4243
  author: Linda
  author_email: yzj0026@auburn.edu
  author_url: ''
  date: '2015-02-02 20:27:53 -0600'
  date_gmt: '2015-02-02 20:27:53 -0600'
  content: Thank you Jeff for your detailed info.
- id: 4258
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2015-02-04 17:14:19 -0600'
  date_gmt: '2015-02-04 17:14:19 -0600'
  content: "[&#8230;] equals Method Java Comparable Interface Java Comparator Interface
    Java Iterator Java Generics Setup JUnit in [&#8230;]"
---
Data structures and collections help us organize data in our program. For example, the [`TreeSet`](http://docs.oracle.com/javase/7/docs/api/java/util/TreeSet.html) class is a collection data structure that always keep the objects sorted, and the [`Stack`](http://docs.oracle.com/javase/7/docs/api/java/util/Stack.html) class always keep the last object added at the front. Both classes are data structures built into the Java standard library

When we write a data structure or an algorithm, it may be useful to keep them generic so that the same data structure can be used for different data types. **Generics** is a feature in Java allows us to write generic algorithms and data structures, and at the same time offers type-safety at compile time. In fact, both `TreeSet` and `Stack` implement generics. In this article, we see how generics work and how to write general data structures. Generics was added in Java 5 (1.5).

## Before Generics

It is possible to write generic collections without generics. Before the introduction of generics in Java 1.5, built-in collections use the most general data type, the `Object` class. As we mentioned in the article [Java Inheritance](http://codenuggets.com/2015/01/13/java-inheritance/), every class inherits from the `Object` class, so any type can be stored in these collections that take object of `Object` as data type.

For example, the `ArrayList` class before Java 1.5 may have methods similar to the following that work with objects of `Object`.

{% highlight java %}
public class ArrayList {
    public boolean add(Object o) { ... }
    public Object  get(int index) { ... }
    public Object  remove(int index) { ... }
    //Other methods ...
}
{% endhighlight %}

This approach works fine; however, if a programmer is not careful and add an object of the wrong type into the list, an error is introduced. The follow example program outputs the length of a list of String objects, but because an object of Integer was added to the list, the program exited with exception.

{% highlight java %}
import java.util.*;

public class ObjectList {
    public static void main(String[] arsgs) {

        ArrayList list = new ArrayList();
        list.add("Hello"); list.add("good"); list.add(1); list.add("morning");

        for(Object o : list) {
            String s = (String) o;
            System.out.println("Length of " + s + " is " + s.length());
        }
    }
}
{% endhighlight %}

```
Output:
Length of Hello is 5
Length of good is 4
Exception in thread "main" java.lang.ClassCastException: java.lang.Integer cannot be cast to java.lang.String
	at ObjectList.main(ObjectList.java:7)
```

Notice that the compiler did not catch this type-safety error because the list takes data of type `Object`. Since both `String` and `Integer` are of type `Object`, this program is perfectly legal for the compiler.

What we need is to keep our collections generic so it can be used with any types, but also be able to specify the type we will add to the collection so that the compiler can check it for us. This is how Java generics work.

## Type Parameter

Generic programming (using generics) is accomplished using type parameters. A type parameter is a placeholder in our class for a data type. When someone uses our generic class, that person will specify the actual type and replace the type parameter. This concept is similar to method parameter variables, which are placeholders for actual values that are passed in when a method is called. Type parameters are defined using <>.

The following example defines a simple generic class, `Node`, which defines one type parameter `<T>`.

{% highlight java %}
public class Node<T> {
    Node parent;
    T value;
    
    public Node(T value, Node parent) {
        this.value = value;
        this.parent = parent;
    }

    T getValue() {
        return value;
    }
}
{% endhighlight %}

Note that because the type parameter `<T>` is defined at the class level, it can be used throughout the class.

## Generic Type Instantiation

During instantiation, we specify the actual type for type parameters. However, only reference types can be used. If you want to put a primitive data type in a generic collection, you'll have to use one of the [wrapper classes](http://docs.oracle.com/javase/tutorial/java/data/numberclasses.html).

The following code uses our generic `Node` class.

{% highlight java %}
public class LinkedNodeExample {
    public static void main(String[] args) {
        Node<Integer> node1 = new Node<Integer>(1, null);
        Node<Integer> node2 = new Node<Integer>(2, node1);
    }
}
{% endhighlight %}

We use `<Integer>` to specify the type we want to use and to replace the type parameter <T>`. Note that we have to do this twice; once when declaring the variable, and once when calling the constructor.

As we mentioned earlier with generics, compiler actually checks for correct type for us. For example, the following does not compile, because we intend to use `Integer`, but we're passing in a `String` into our constructor.

{% highlight java %}
public class NodeWrongType {
    public static void main(String[] args) {
        Node<Integer> node = new Node<Integer>("Hello", null);
    }
}
{% endhighlight %}

```
error: constructor Node in class Node<T> cannot be applied to given types;
        Node<Integer> node = new Node<Integer>("Hello", null);
                             ^
  required: Integer,Node
  found: String,<null>
```

The compiling error basic says that the `Node` class requires an `Integer`, but a `String` is found.

## Bounded Type Parameter

When we define a type parameter, any type can be used to take place of the type parameter. However, Java also allow us to limit the types we can use as parameter through `extends` keyword. This is called bounded type parameters.

The following example shows a generic `Node` class that only takes numeric types (types that extends Number class: Integer, Float, Long, Double, etc).

{% highlight java %}
public class Node<T extends Number> {
    Node parent;
    T value;
    
    public Node(T value, Node parent) {
        this.value = value;
        this.parent = parent;
    }

    T getValue() {
        return value;
    }
}
{% endhighlight %}

The following version of the `Node` class only take types that implements the `Comparable` interface.

{% highlight java %}
import java.util.Comparable;
public class Node<T extends Comparable<T>> {
    Node parent;
    T value;
    
    public Node(T value, Node parent) {
        this.value = value;
        this.parent = parent;
    }

    T getValue() {
        return value;
    }
}
{% endhighlight %}

Note that the `Comparable` interface is also an generic interface, so that we need to use `Comparable<T>` to bind a type.

## Generic Method

Methods can also be generic. The following generic method finds the index of `target` in the array `a`. If `target` is not found, -1 is returned.

{% highlight java %}
public class Util {
    public static <T> int search(T[] a, T target) {
        for(int i = 0; i < a.length; i++)
            if(a[i].equals(target))
                return i;
        return -1;
    }
}
{% endhighlight %}

Two things to notice:

1. Notice the syntax to define type parameters for a method is slightly different from the syntax for a class (or interface).
2. Also, `<T>` is only defined at the method level, so it's only accessible in the compare method.

The following code calls the `search()` method.

{% highlight java %}
public class GenericMethodCall {
    public static void main(String[] args) {
        Integer[] a = {1, 2, 3};
        int result = Util.<Integer>search(a, 2);
        System.out.println("Target is found at index " + result);
    }
}
{% endhighlight %}

```
Output:
Target is found at index 1
```