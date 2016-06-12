---
layout: post
status: publish
published: true
title: Java Program Basic Structure
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1023
wordpress_url: http://codenuggets.com/?p=1023
date: '2014-08-09 05:38:04 -0500'
date_gmt: '2014-08-09 05:38:04 -0500'
categories:
- Programming
- Java
tags: []
comments:
- id: 3418
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2014-08-26 17:52:32 -0500'
  date_gmt: '2014-08-26 17:52:32 -0500'
  content: "[&#8230;] Step Java Program Basic Structure Java Date Types Java [&#8230;]"
- id: 3419
  author: Java Date Types | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-date-types/
  date: '2014-08-26 18:12:22 -0500'
  date_gmt: '2014-08-26 18:12:22 -0500'
  content: "[&#8230;] This article explains most commonly used types for declaring
    variables. If you wish to learn what are variables and how to declaring them,
    please see the previous article, Java Program Basic Structure. [&#8230;]"
---
This article covers the basic structure of a Java program. The concepts that will be covered in this article are: classes, methods, variables, and basic output.

## Classes

Java is an object-oriented (OO) programming language -- that means a Java program is organized in one or more objects. A class defines how a set of objects behave (like a blueprint of objects). A class is also a container for Java code in the sense that all Java code is written in classes. A program usually consists of multiple classes, each implements different functionality of the program.

It's very simple to define a class:

1\. Make a new text file, named `MyClass.java`, in your project folder

2\. Open the new file in a text editor and write your class definition:

{% highlight java %}
public class MyClass {
}
{% endhighlight %}

That's all your need to define a class. The open brace `{` signifies the start of the class and the close brace `}` signifies the end.

You can put more than one class in the same `.java` file; however, each `public` class must be in a file with same file name as the class name.

## Methods

A Method is a reusable unit of code that goes into a class. Methods are sometimes called functions in non-object oriented languages (like C), but when defined in a class, the proper term is <em>method</em>.

A method is usually used to define a reusable algorithm, or instructions of doing something. A method can take parameters as inputs and return a value as the result of computation as output. The following example defines a method, called `factorial`, that takes one parameter named `n` (of type integer) and returns an integer that is the factorial of `n`. Note `factorial(5) = 1 * 2 * 3 * 4 * 5`, where `*` is multiplication in Java.

{% highlight java %}
public class MyClass {
    int factorial(int n) {
        int result = 1;
        for(int i = 0; i <= n; i++)
            result = result * i;
        return result;
    }
}
{% endhighlight %}

With this method defined, when we need to compute factorial of a number, we do not need to rewrite this code; instead, we just call the method.

### The main() Method

The `main()` is a special method in Java that starts the execution of the program. When you ask Java to run a program, the Java virtual machine will search for this method and start execution from the first line of this method. If not found, the program will not run.

The following code shows the signature of this method.

{% highlight java %}
public class MyClass {
    public static void main(String[] args) {
        System.out.println("Hello!");
    }
}
{% endhighlight %}

This simple program only outputs "Hello!" to the monitor and exits.

### Calling a Method

Now we know how to define methods, let see how to call a method. We will use the `factorial` method we defined previously. The following simple program outputs the factorial for 3, 4, and 5.

{% highlight java %}
public class MyClass {
    /** The entry point of the program */
    public static void main(String[] args) {
        System.out.println("The factorial of 3 is " + factorial(3));
        System.out.println("The factorial of 4 is " + factorial(4));
        System.out.println("The factorial of 5 is " + factorial(5));
    }

    /** Computes the factorial of n */
    int factorial(int n) {
        int result = 1;
        for(int i = 0; i <= n; i++)
            result = result * i;
        return result;
    }
}
{% endhighlight %}

Notice how short the program is. Simple right?

## Variables

A program needs to be able to store and access data in memory. These data represent the state of your program. For example, a racing game must keep track of the speed of cars and the time of the race. These are the data or state of the game. Variables represent memory locations to store our data.

### Declaring a Variable

To use a variable, we have to first declare its type. The syntax to declare a variable follows.

```
type var_name = value;
```

Intuitively, `var_name` is chosen by you and should follow the rule of naming a Java <em>identifier</em>:

- Identifiers must be composed of letters, numbers, the underscore _ and the dollar sign $.
- Identifiers may only begin with a letter, the underscore or a dollar sign.

As an convention, variable name follow camel case and begin with lower case letter. For example: `backColor`, `bankBalance`.

### Common Data Types

Data types in Java will be covered in detail in another article. Here we list some common data variable types.

- Integer numbers types: these are whole numbers. For example, 123, 0, -1.
    - `int`
    - `long`
- Decimal numbers types: these are also called real numbers For example 3.13, -1.05, 0.05.
    - `float`
    - `double`
- Logic type: represent true or false.
    - `boolean`</ul>
- Textual types: represent a character or a string of text. For example 'a' or "Hello".
    - `char`: represent a single character
    - `String`: represents multiple characters
- Array: a collection variable of the same type.
- `void`: represents that a method does not return a value.

### Local Variables

When a variable is declared inside a method, it is called a local variable, because it can only be accessed inside that method. We have already used local variables in our `factorial` method above.

- `result` is declared of type `int` that holds our return value.
- `n` of type `int`. Method parameters are also local variables.
- `i` of type `int` is also a variable. Loops will be covered in later articles.

### Instance Variables

When a variable is declared inside a class, but outside of a method it is called an instance variable, or a member variable. The effect of an instance variable is that any method inside the class can access this variable. In OO design, if this variable is declared `public` code outside of this class can access it as well.

The following example declares 2 instance variables, `x` and `y`, and two methods `distance()` and `subtract()`. Both methods can access the two instance variables.

{% highlight java %}
public class Point {
    int x, y;

    /** Compute distance between two points */
    double distance(int x2, int y2) {
        return Math.sqrt((x2 - x) * (x2 - x) + (y2 - y) * (y2 - y));
    }

    /** Subtract this point by a second point. */
    void subtract(int x2, int y2) {
        x = x - x2;
        y = y - y2;
    }
}
{% endhighlight %}

## Comments

Comments are the texts in your program source file that will be ignored by the Java compiler. Comments are little memos programmers put in source files as reminders or for other programmers. They usually briefly explain what a piece of code does and you can put anything in a comment.

Java inherit the syntax of comments from C and C++. There are 3 types of comments:

1. Single-line comment: `//` to the end of the line is comment.
2. Multi-line comment: `/*` to `*/` is comment.
3. Javadoc comment: when place before a class or method `/**` to `*/` is Javadoc.

The following snippets shows examples of Java comments.

{% highlight java %}
/** This is a Javadoc that describe the class. */
public class MyClass {
    /**
     * This is Javadoc comment that describes the method, factorial.
     * @param n description of n
     * @returns describe what will be returned 
     */
    int factorial(int n) {
        /* This is a block comment
           which spans multiple lines
        */
        int result = 1;
        for(int i = 0; i <= n; i++)
            result = result * i; //This is a line comment
        //Another line comment
        return result;
    }
}
{% endhighlight %}

## Output to Screen

The simplest form of output is writing text to the monitor inside a terminal (or command prompt for Windows). Java made this task really easy. We can use the built-in object`System.out` for this task (where `System` is the class and `out` is an object).

The following example shows how to output text to the monitor.

{% highlight java %}
public class MyClass {
    public static void main(String[]) {
        //Use println() to output text followed by line break
        System.out.println("This is a line by itself");

        //Use print to output text without line break
        System.out.print("Hello, my name is ");
        System.out.print("John");
    }
}

/*
Output

This is a line by itself
Hello, my name is John
*/
{% endhighlight %}