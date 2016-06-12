---
layout: post
status: publish
published: true
title: Java Interface
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 885
wordpress_url: http://codenuggets.com/?p=885
date: '2014-06-20 18:16:58 -0500'
date_gmt: '2014-06-20 18:16:58 -0500'
categories:
- Programming
- Java
tags:
- Java
- interface
- polymorphism
- abstract class
comments:
- id: 3457
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2014-09-03 03:26:09 -0500'
  date_gmt: '2014-09-03 03:26:09 -0500'
  content: "[&#8230;] First Step Java Program Basic Structure Java Data and Data Types
    Java Interface [&#8230;]"
---
Last time, we covered <a href="http://codenuggets.com/2015/01/20/java-abstract-class/">abstract classes</a>. In this article, we are going to cover a similar concept called interface (not the same as a <a href="http://en.wikipedia.org/wiki/Graphical_user_interface" target="_blank">graphical user interface</a>).

An interface in Java is like an abstract class; however, while an abstract class may contain methods without a body, none of the methods in an interface has a body. In other words, an interface contains a list of method definitions. It defines what methods a class should have, but does not provide the code. An interface is also called a contract. 

## Real World Analogy

Let's consider a real-world analogy of interface: the power socket. A power socket is an interface for electric appliances because it defines a list of specs. In the U.S. an outlet must provide voltage around 120 V, and frequency of 60 Hz.

Any appliance conforms to this specs can be plugged into the socket.

## Defining an Interface

Coming back to Java, the following defines an interface named `Bag`.

{% highlight java %}
interface Bag
{
    void add(int item);
    int  remove();
}
{% endhighlight %}

Each interface is usually saved in one `.java` file with the name matching the interface name. So save this interface in a file name `Bag.java`

## Implementing an Interface

A class implements an interface using the **`inteface`** keyword. A class that implements the interface must provide the code for all the methods (specs) listed. For example, the `ArrayBag` class below implements the `Bag` interface:

{% highlight java %}
class ArrayBag implements Bag {
    int pos = 0;
    int[] items = int[10];
    
    void add(int item) {
        if (pos < items.length - 1) {
            items[pos] = item;
            pos++;
        }
    }

    int remove() { 
        //code for remove
    }
}
{% endhighlight %}

Notice the `ArrayBag` class must have all the methods listed in the `Bag` interface and their code. Other classes that uses our `ArrayBag` class knows how to to use it because `ArrayBag` follows the spec in `Bag`. In terms our analogy:

1. The interface <=> the specs of the socket
2. The class that implements the interface <=> the actual socket
3. And other classes that use our class <=> appliances

In a sense, a Java interface is a blueprint for classes.

## Failure to Comply

What if a class implements an interface but does not have all the methods listed in the interface? In this case the class does not conform to the spec. In real world, if a socket does not follow the spec, it could damage our gadget. In Java, the compiler will catch this error and your program will not compile.

## Polymorphism with Interface

Yes we can do <a href="http://codenuggets.com/2015/01/18/java-polymorphism/">polymorphism</a> using interfaces. What this mean is that we can create a variable of an interface, and assignment to it an object of any class that implements the interface.

We often see interfaces being used as parameter and return types, as shown below.

{% highlight java %}
class ArrayUtil {
    public static void sort(int[] a, Comparator c) {
        //Method body here
    }
}
{% endhighlight %}

Note: `Comparator` is an interface.

Obviously we cannot create an instance of an interface types, so what do we pass into the sort() method for parameter `C`, which has an interface type? We can pass in an instance of any class that implements the `Comparator` interface, as shown below:

{% highlight java %}
class Main {
    public static void main(String[] args) {
        int[] a = {5, 1, 2, 4};
        MyComparator myComp = new MyComparator();
        ArrayUtil.sort(a, myComp);
    }
}

class MyComparator implements Comparator {
    //Class body here
}
{% endhighlight %}

Last, why would we even want to use interface parameters? Why don't we just always use class types as parameters? Well, since an interface defines what methods are included in a class, that is all we really need to interact with a class, and we don't need to know how those methods are implemented.

The beauty of this is that we can have two classes that implement an interface in two completely different ways, but as long as these classes implement the methods, they can passed to an interface parameter. Car engines don't have to be designed the same way, but as long as they follow certain specs, they are reusable components.