---
layout: post
status: publish
published: true
title: Java Classes and Objects
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1101
wordpress_url: http://codenuggets.com/?p=1101
date: '2014-11-07 22:31:33 -0600'
date_gmt: '2014-11-07 22:31:33 -0600'
categories:
- Programming
- Java
tags: []
comments:
- id: 3980
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2014-11-17 01:25:22 -0600'
  date_gmt: '2014-11-17 01:25:22 -0600'
  content: "[&#8230;] Step Java Program Basic Structure Java Data and Data Types Java
    Classes and Objects Java Arithmetic Operators Java Data and Data Types 2 Java
    [&#8230;]"
- id: 4139
  author: Java Method Overloading | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2015/01/05/java-method-overloading/
  date: '2015-01-05 05:33:46 -0600'
  date_gmt: '2015-01-05 05:33:46 -0600'
  content: "[&#8230;] we covered the basics of writing classes and method in this
    article. Because object-oriented-programming (OOP) concepts are such an important
    topic in Java, [&#8230;]"
- id: 4154
  author: Java Constructor and Initilization Method | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2015/01/07/java-constructor-and-initilization-method/
  date: '2015-01-07 18:00:22 -0600'
  date_gmt: '2015-01-07 18:00:22 -0600'
  content: "[&#8230;] our earlier article Classes and Objects, we showed how to write
    a constructor for a simple class. In this article, we are going to dive [&#8230;]"
---
You may have heard that Java is an object-oriented programming language (OOP), but what exactly does that mean? This means that Java supports the concept of objects and a program consists of a collection of objects interacting with each other.

Java is also purely objected-oriented. What does this mean? You may have worked with other programming languages such as (C, PHP, or assembly). In these languages, programs are a list of instructions, organized linearly or divided into functions (no concept of objects). This is no so in Java. Objects are basic units of code in Java, and no code (instruction) is allow outside an object; in other words, all of our code reside in one class or another.

The purpose of this article is to cover the basic OOP concepts in Java.

## What are Objects?

An object is simply a concept, in our program, for which we can keep track of and manipulate its states. For example, in a racing game, we may have an object that represents a car. This object may have a car's current speed, acceleration, fuel level, etc. These states are defined as the object's **member variables**. The car object may also have behaviors to manipulate the car. For example, we can have behaviors called `speed_up()` and `break()`, that increase and reduces the car's speed and acceleration. Behaviors are called **methods** in Java.

In Java (being purely OOP), the program itself is a special object, which contains a special method named `main()`. This object starts the program and control interaction between objects. The follow figure shows this example.

<center><img src="http://codenuggets.com/wp-content/figures/java-classes-and-objects/car_obj.png" /></center>

An object does not have to reflect a real-world concept. For example, rectangles, imaginary numbers are a few abstract concepts that can also be modeled in program using objects.

## Defining Class

The term **class** means the type of object. We create objects by first defining (writing the code of) a class. Then we can create multiple objects of the same class, just like the car example where we have 2 cars created from the same Car class.

In this section we are going to write a simple `Rectangle` class. Each class should be in it's own file with the file name matching the class name. So make a new file `Rectangle.java` and open in your favorite editor.

The class has 2 member variables, `width` and `height`, both integers. We're going to add one rule that the `width` must be greater than `height`. The class will also contain one method `area()`, which computes and returns the area of the rectangle.

<center><img src="http://codenuggets.com/wp-content/figures/java-classes-and-objects/rec_class.png" /></center>

We are going to write this class in simple steps: define class, member variables, method, constructor, class instantiation.

1\. **Define class**. In this step, we're just going write the shell of the class and just says we are going to call our class `Rectangle`. The keyword `public` is visibility of this class which will be covered in the next section.

{% highlight java %}
public class Rectangle
{

}
{% endhighlight %}

2\. **Member variables**. In this step we're going to add member variables to our class. In this class we only have two, both of type integer: `width` and `height`.

{% highlight java %}
public class Rectangle
{
    private int width;
    private int height;
}
{% endhighlight %}

Member variables represents the states of objects and could be different for each Rectangle object.

3\. **Method**. In this step we're going to add the `area()` method (line 6-9 below).

{% highlight java %}
public class Rectangle
{
    private int width;
    private int height;

    public int area()
    {
        return width * height;
    }
}
{% endhighlight %}

Methods have the following parts:

1. Visibility modifier: our method is `public` so other objects can call this method.
2. The return type: Our method returns a value of type `int`. If a method does not return a value, the return type should be `void`
3. The method name: this can be anything following rule of identifiers. Method names usually follows camel case convention with first letter lower case.
4. The parameter list in parenthesis: a comma-delimited list of input parameters, preceded by their data types. Our method has no parameters, so it's just empty parentheses `()`.
5. The method body, enclosed between braces

Our method is very simple; it simply returns an integer which is just width multiply by height.

4\. **Constructor**. Our class is nearly complete with variables to keep the state of an object and method to manipulate the state. One question is, how do we initialize our variables in the first place? In other words, how do we put values into `width` and `height`. If these variables are declared `public`, then we can set them directly, but this is not safe and could break our rule that `width` must be greater than `height`
The way we initialize our object is through a constructor. Constructor is a method that

1. Has the same name as the class.
2. Does not have a return type, because what it returns is an instance object of the class.

The following code shows the constructor, which throws an error `IllegalArgumentException`, when `width` is not greater than `height`. In Java, errors are raised using `Exceptions`, which will be covered in later articles.

{% highlight java %}
public class Rectangle
{
    private int width;
    private int height;

    // A constructor
    public Rectangle(int width, int height)
    {
        if(width <= height)
            throw new IllegalArgumentException()
        
        this.width  = width;
        this.height = height;
    }

    public int area()
    {
        return width * height;
    }
}
{% endhighlight %}
In the code above, the `this` keyword refers to the member variables. Without the `this` keyword, `width` and `height` refers to the parameters of the constructor.

The constructor is simple. It first checks if `width` is less than or equals to `height`. If so, then raise error; else initialize member variables with the parameters passed in.


5\. **Instantiation**. Congrats, our class is complete! Now we are going to write a short program and create a couple of objects of our Rectangle class. The technical term for creating an object is called **instantiation**.
As we said earlier, our program is also an object with a special method named `main()`. We are going to call our class `AreaComputer`.

{% highlight java %}
public class AreaComputer
{
    public static void main(String[] args)
    {
        Rectangle rect1 = new Rectangle(10, 5);
        Rectangle rect2 = new Rectangle(20, 10);
        System.out.println("Area of rectangle 1 is " + rect1.area());
        System.out.println("Area of rectangle 2 is " + rect2.area());
    }
}
{% endhighlight %}
The output of our program follows.

```
Area of rectangle 1 is 50
Area of rectangle 2 is 200
```
The program creates two instances (objects) of the `Rectangle` class by using the **`new`** keyword. This keyword calls our constructor, which in turn initializes our objects.

After the objects are constructed, the area of the rectangles are computed by calling the `area()` method. And the areas are printed out using standard output.

## Visibility Modifiers

In the previous code examples, you have seen that the class and member variables are preceded with either with `public` or `private` keywords. These are the **visibility modifiers** (also called access modifiers). These modifiers specifies which part of program can access which variables or call which methods. They make our program more reliable and secure.

The reason we have these modifiers is to restrict access of parts of our class by code written by other people. For example, in our `Rectangle` class, we know the there is a rule that the width must be greater than the height. If we do not restrict the access of these variables, any other object can change the values of these two variables, which would break our rules.

Modifiers can be applied to class, member variables, and methods. The following only covers modifiers to class members (variables and methods). Modifiers for classes has to do visibility of classes in packages. The modifiers follows:

1. **`public`**: any code or object can access (read and write) the variable or call the method.
2. **`protected`**: only method in the same class and subclasses can access the variable or method.
3. **`protected`**: this is the most strict; only method in the same class has access.
4. **No modifier**: Any code in the same package (folder) has access.

## Static Modifier

In addition to the access modifiers, we can also add the `static` modifier to class members (variables and methods). We have already seen a `static` method in our previous example: every `main()` method is a static method.

Static members have the following properties:

1. You don't have to create an instance of a class to use its static members.
2. Static member variables are shared among all instances of the same class.
3. Static methods may not use or call non-static members.

The rationale for static members is that we don't have to create an instance of the class to use a static method or variable. If we follow this logic, then rule 3 become obvious: because we don't have an instance of the class, non-static member variables do not exist, so we static method cannot use them. However, static member variables always exists even without an instance, so an static method can use a static variable.

Static methods are useful for utility function, for example mathematics functions such as `Math.sin()`. We don't need to create an instance of the `Math` class to use the `sin()` function. This makes our code shorter and more concise.

## Importing Classes

Java is not only a language; it is also a library of large collection of classes for us to you. These classes are part of the JDK and we often call them the Java API. There are classes from common data types to classes that generates random numbers and sorting arrays.

The classes in the API are divided into packages. The most commonly used classes, such as basic data types and the `Math` class, are located in the `<a href="http://docs.oracle.com/javase/7/docs/api/java/lang/package-summary.html" target="_blank">java.lang</a>` package. You do not have to explicitly import the classes in this package to use them; they are implicitly imported into every program.

There are plenty of other packages and classes that can be imported. We will introduce more classes and packages as we explore more aspects of Java. For the curious, the API documentation can be found <a href="http://docs.oracle.com/javase/7/docs/api/overview-summary.html" target="_blank">here</a>.

To import a class or package, we use the `import` statement at the top of our .java file. Here we give an example of using the `Random` class located in the `java.util` package to generate random rectangles. To do so we simply add another parameterless constructor to our class.

{% highlight java %}
import java.util.Random;
import java.io.*;

public class Rectangle
{
    private int width;
    private int height;

    // A parameterless constructor
    public Rectangle()
    {
          Random rand = new Random();    //Create a new Random object
          width = rand.nextInt();        //Get a random integer
          height = width + rand.nextInt; //Set height to width + another random integer
    }

    // A constructor
    public Rectangle(int width, int height)
    {
        if(width <= height)
            throw new IllegalArgumentException()
        
        this.width  = width;
        this.height = height;
    }

    public int area()
    {
        return width * height;
    }
}
{% endhighlight %}

The first line of the file imports the Random class. We can also import the entire package by replacing the class name with a *, as shown in line 2.