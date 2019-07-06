---
layout: post
status: publish
published: true
title: Java Data and Data Types 2
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1079
wordpress_url: http://codenuggets.com/?p=1079
date: '2014-10-22 20:44:33 -0500'
date_gmt: '2014-10-22 20:44:33 -0500'
categories:
- Programming
- Java
tags: []
comments:
- id: 3805
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2014-10-23 22:21:34 -0500'
  date_gmt: '2014-10-23 22:21:34 -0500'
  content: "[&#8230;] Step Java Program Basic Structure Java Data and Data Types Java
    Data and Data Types 2 Java [&#8230;]"
- id: 4113
  author: Java Boolean Expressions | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/12/27/java-boolean-expressions/
  date: '2014-12-27 21:44:56 -0600'
  date_gmt: '2014-12-27 21:44:56 -0600'
  content: "[&#8230;] operators can also be used to compare variable of reference
    types (objects); however, when used, these operators performs reference (address)
    comparison. For [&#8230;]"
---
In the previous article, <a href="http://codenuggets.com/2014/08/26/java-date-types/" target="_blank">Java Data and Data Types</a>, common data types are introduced. Programmers use these types to define variables to track states of a program (for example, car speed). In this article, we study Java data types in more detail and explain two broad categories in Java's type system, primitive and references types, and how they are represented in memory.

This is a very fundamental topic in Java and paramount in learning Java.

## Primitive Types

Most of the types mentioned in the previous article types are primitive types, which are the most basic data types in java. Primitive types are: `byte`, `short`, `int`, `long`, `float`, `double`, `char`, and `boolean`.

Primitive types also have the properties that they are fixed sized, such that all variable of the same type use the same amount of memory, and "indivisible", such that they are not composed of other types.

Conceptually, computer memory is a set of storage cells, each with an address. For example, the figure below shows a block of memory with address from `100` to `104`

<img src="/images/figures/java-data-and-data-types-2/memory.png" />

When a variable of a primitive type is declared, `int myInt = 10;` for example, this variable represents a memory location. In the figure below, `myInt` represent memory location `102` and we can use `myInt` to store to and read from this memory location. In addition, when the program is compiled, all occurrences of `myInt` is replaced with memory address `102`. For example, when we write the statement `myInt = 10;`, it literally means, set the content of memory location `102` to integer `10`.

<img src="/images/figures/java-data-and-data-types-2/memory-primitive.png" />

## Reference Types

Reference types are any class types and arrays. These include the `String` class, and any class you write. The reason that these are called reference types is because, in contrast to primitive types, a variable (memory location) of this type holds a **memory address** to the data, instead of the data itself. We give an example below.

Let's say we have this statement in our program: `String s = "Hello";`

What this statement does is assign a memory location to `s`, but the location does not store the string `"Hello"`, but the address of it, as shown in the figure below. In the figure, `s` represents memory address `101`. However, at this location, the location of the string `"Hello"` is stored which is at location `150`.

<img src="/images/figures/java-data-and-data-types-2/memory-reference.png" />

Also note that objects (the actual data) may take more than 1 memory locations. In fact, some data may take many memory locations (use lots of memory) as in a long array. One justification for storing references instead of the actual data is that since the compiler does not know how large the actual data will be when the program is executed, JVM has to find a memory location large enough for the data during runtime.

In the following code snippet, we are not copying the content of `a` to `b`, but only copying the address.

{% highlight java %}
String a = "Hello";
String b = a;
{% endhighlight %}

## Object Instantiation

Instantiation mean to create an object from a class. For example, the following code performs two instantiations: one of `String` and one of `Person`.

{% highlight java %}
String s = "Hello";
Person p = new person();
{% endhighlight %}

Each of above actually take two steps. The first step is **declaration**, where a variable of the desired type is declared. The second step is the actual **instantiation**, where the object is created, as shown below. 

{% highlight java %}
Person p;         //declaration; p = null
p = new person(); //instantiation
p = null;         //reset the variable to null
{% endhighlight %}

After the first step (and before the second step) is performed, the variable `p` holds the value of `null`, which is a special value that can be assigned to variables of references types and means the variable does not point to any object. If we call any method or field of this variable at this point, we will get the error `NullPointerException`.

The second step does the following:

1. Ask Java to find a block of memory large enough for the Person object
2. Create the object
3. Return the address of the object
4. Put the address in varaible p


After the second step, methods of the object can be safely called.

## Object of Other Objects

Often we have objects that are composed of other objects. For example, in the following code, we have a `Person` class, which contains another object of type String. The following figure shows how an object of Person class is presented in memory, when a variable, `p`, is declared.

{% highlight java %}
class Person {
    int id;
    String name;

    public Person(int id, String name) {
        this.id = id;
        this.name = name;
    }
    //...
}

Person p = new Person(1, "John");
{% endhighlight %}

<img src="/images/figures/java-data-and-data-types-2/memory-person.png" />

Note that arrays are also reference types. The following figure shows how an array of objects are stored.

{% highlight java %}
String[] names = {"Abe", "Bob", "Cid"};
{% endhighlight %}

<img src="/images/figures/java-data-and-data-types-2/memory-array.png" />