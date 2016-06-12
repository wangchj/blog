---
layout: post
status: publish
published: true
title: Java Exception
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1412
wordpress_url: http://codenuggets.com/?p=1412
date: '2015-01-28 23:26:10 -0600'
date_gmt: '2015-01-28 23:26:10 -0600'
categories:
- Programming
- Java
tags:
- exception
- throw
- try
- catch
- finally
- ArithmeticException
- exception propagation
comments: []
---
During runtime (execution), our program sometimes encounter unforeseen errors. For example, our program may be in the middle of reading a file from disk when the disk crashed and we can no longer proceed to read the file. In unforeseen situations like this, the JVM would notify our program of the error by throwing an Exception object describing the error.

The exception gives our program a chance to handle the error by catching it. If our program does not handle the exception, the program will exit (crash) with error message output to the screen.

In addition to exception raised by JVM, our program can also explicitly throw exceptions, signifying an error scenario. Exceptions thrown by our program is handled the same way as the exceptions thrown by JVM. In this article, we cover how exception mechanism works in Java.

## Exception

The following short program causes an `ArithmeticException` to be thrown because of division by zero.

{% highlight java %}
public class DivByZero {
    public static void main(String[] args) {
        int count = 10 / 0;        //Exception thrown here
        System.out.println("End"); //Never printed
    }
}
{% endhighlight %}

```
Output:
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at DivByZero.main(DivByZero.java:3)
```

Note that the program immediately stops at the point where the exception was thrown; so, the print statement in the program above (and anything that follows) is never executed.

## Throw Statement

In the same way, our program can explicitly throw an exception using the `**throw**` statement. The following method throws an IllegalArgumentException when the parameter is less than 0, assuming we have a `Square` class.

{% highlight java %}
public class ShapeMaker {
    public static makeSquare(int width) {
        if (width < 0)
            throw new IllegalArgumentException("Width less than 0.");
        return new Square(width);
    }
}
{% endhighlight %}

In the code above, the exception is throw in line 4 with the message `"Width less than 0."`.

Notice that we are actually creating an exception object using the `new` operator. The reason that exceptions are object is because they contain specific information about the error, such as the message, error code, etc.

## Try and Catch

We can handle an exception by using `try` and `catch` blocks. A `try` block contains a piece of code that we think could throw an exception. When an exception occurs in a `try` block, the control of the program is jump to a `catch` block, as shown in the example below.

{% highlight java %}
public class TryAndCatch {
    public static void main(String[] args) {
        int dividend = 10, divisor = 0;
        try {
            System.out.println("Result of division is " + (dividend / divisor));
        }
        catch(IllegalArgumentException e)
        {
            System.out.println("IllegalArgumentException is thrown.");
        }
        catch(ArithmeticException e)
        {
            System.out.println("ArithmeticException is thrown.");
        }
    }
}
{% endhighlight %}

```
Output:
ArithmeticException is thrown.
```

In the code above, an exception was thrown at Line 5 and the control of the program is transferred to a `catch` block. Notice that we can have multiple `catch` blocks per `try` block, as shown above. Java will pick the first compatible exception type, which in this case is `ArithmeticException`

## Finally

Try and catch can have an optional `finally` block. The code inside a `finally` block is executed regardless an exception was thrown in the `try` block or not. This block is usually used to clean up resources, such as network connections and opened files. If used, the `finally` block must follow `catch` blocks.

The following code shows an example of a try-catch-finally statement.

{% highlight java %}
public class TryCatchFinally {
    public static void main(String[] args) {
        for(int dividend = 10, divisor = 1; divisor >= 0; divisor--) {
            try {
                System.out.println("Result of division is " + (dividend / divisor));
            }
            catch(ArithmeticException e) {
                System.out.println("ArithmeticException is thrown");
            }
            finally {
                System.out.println("Finally");
            }
        }
    }
}
{% endhighlight %}

```
Output:
Result of division is 10
Finally
ArithmeticException is thrown
Finally
```

## Exception Propagation

If an exception is not caught with a try-catch clause in the method where it's occurred, it is sent to the caller of the method. If the caller method still does not catch the exception, it is further propagated to its caller. When an exception reaches the `main()` method of the program and it is still not caught, it cause the program to end.

The following program shows an example where exception is thrown in method `b()` and is propagated to and caught in method `a()`.

{% highlight java %}
public class ExPropCaught {
    public static void main(String[] args) {
        a();
    }
    
    public static void a() {
        try {
            b();
        }
        catch(Exception e) { System.out.println("Exception caught in a()."); }
    }

    public static void b() {
        int count = 10 / 0; //Throws ArithmeticException
    }
}
{% endhighlight %}

```
Output:
Exception caught in a().
```

Conversely, the exception in the following program is never caught, causing the program to crash and output the error message.

{% highlight java %}
public class ExPropNotCaught {
    public static void main(String[] args) {
        a();
    }
    
    public static void a() {
        b();
    }

    public static void b() {
        int count = 10 / 0; //Throws ArithmeticException
    }
}
{% endhighlight %}

```
Output:
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at ExPropNotCaught.b(ExPropNotCaught.java:11)
	at ExPropNotCaught.a(ExPropNotCaught.java:7)
	at ExPropNotCaught.main(ExPropNotCaught.java:3)
```

## Exception Hierarchy

The following figure shows the exception class hierarchy.

<center><img src="http://docs.oracle.com/javase/tutorial/figures/essential/exceptions-throwable.gif" /></center>

As seen in the figure, any object that can be thrown to signify an error condition in our program is a subclass of the `Throwable` class. According to Java documentation, difference between Error and Exception is the following.

<blockquote>
When a dynamic linking failure or other hard failure in the Java virtual machine occurs, the virtual machine throws an Error. Simple programs typically do not catch or throw Errors. Most programs throw and catch objects that derive from the Exception class. An Exception indicates that a problem occurred, but it is not a serious system problem. Most programs you write will throw and catch Exceptions as opposed to Errors

</blockquote>
## Checked and Unchecked Exceptions

Unchecked exceptions are `Error`, `RuntimeException`, and their subclasses. Unchecked exceptions represent numerous unforeseen runtime errors a program can encounter, such as hardware failures. Since a programmer cannot possibly anticipate all the runtime exceptions (errors) that can be thrown by the system, unchecked exceptions are not required to be documented in our code using the `throws` keyword. In addition, according to the creators of Java language, "unchecked runtime exceptions represent conditions that, generally speaking, reflect errors in your program's logic and cannot be reasonably recovered from at run time."

Checked exceptions are the errors that the programmers anticipate that could happen during runtime. For example, we are writing a method that asks the user to enter using the keyboard the name of a file to open. We would throw an exception is the file with the name does not exist. Since we could anticipate this error when we write our program, we should throw a checked exception. Anything exception that is not unchecked exception is a checked exception.

Checked exception must be caught using a `try` and `catch` blocks, or the method that throws it must be documented with the **`throws` clause**. For example, the following method throws an unchecked exception `Exception`; because the method does not catch the exception, it must have the `throws` clause at the header of the method.

{% highlight java %}
public class CheckedException {
    public static int factorial(int n) throws Exception {
        if(n <= 0)
            throw new Exception("n is negative.");
        int f = 1;
        for(int i = 1; i <= n; i++)
            f *= i;
        return f;
    }
}
{% endhighlight %}

If "`throws Exception`" were omitted, we would get compiling error.