---
layout: post
status: publish
published: true
title: Java Start
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 869
wordpress_url: http://codenuggets.com/?p=869
date: '2014-06-20 15:44:08 -0500'
date_gmt: '2014-06-20 15:44:08 -0500'
categories:
- Programming
- Java
tags: []
comments:
- id: 3233
  author: Java Variables | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/07/23/java-variables/
  date: '2014-07-23 04:17:00 -0500'
  date_gmt: '2014-07-23 04:17:00 -0500'
  content: "[&#8230;] First Step in Java, we covered how to get started on writing
    programs using Java. This article introduces a [&#8230;]"
- id: 3416
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2014-08-26 17:29:11 -0500'
  date_gmt: '2014-08-26 17:29:11 -0500'
  content: "[&#8230;] Java Programming First Step Java Program Basic Structure Java
    Date Types Java [&#8230;]"
---
Welcome to core Java concepts! I am glad you decided to join us to learn how to write programs in Java! This series of tutorials is intended to cover the foundations of Java. We will start from the most fundamental concepts of programming and progress to cover most of Java programming techniques and features. If you have very little or no programming experiences, do not worry! This series will start from the fundamentals. If you are experience with Java, later tutorials of specific topics may be useful to you.

To get start in this first article, we are going to cover a bit of background about Java and what tools we need to write and run Java programs.

## Java Overview

Java is an high-level object-oriented programming language developed by Sun Microsystems around 1991 and first version was released in 1995. One of the main goal of the language is **portability**. What this means is that you can write a Java program using one operating system (OS), let say Windows, and run it on another operating system, Mac OS X for example. The ambitious goal of portability of Java not only exist on the OS level, but programs can also run on completely different processors and hardware architectures. Sun Microsystems was purchased by Oracle in 2010 and is now the official authority of Java language specifications.

What do we mean by that Java is high-level and object-oriented? Being a **high-level language** means that Java hides most of the details of the computer hardware and offers a rich and expressive language grammar for programmers to quickly develop a program. For example, in high-level languages, we don't have to know what kind of central processing unit (CPU) our program is running on, what registers we can use, memory configurations, and etc.

**Object-oriented** programming (OOP) language means that a program is composed of objects interacting with each other. A central idea of OOP is classes, which will be covered in detail in later tutorials. One thing to keep in mind is that Java is composed of the language, and a huge class library (called Java API) available to programmers.

Last, in order to achieve portability, Java is a interpreted language. Java programs are not compiled directly to the machine code that can be run by the processor. Instead, programs are compile into **bytecode** which is ran by Java Virtual Machine (JVM). This is why when we run Java programs, we need to install Java Runtime Environment (JRE), which contains a JVM.

## What is a Program?

A Java program is simply one or more text files with `**.java**` file extension that contain Java instructions. These files are often called source files, or source code, because they contain the code written by programmers. A simple program may only have one source file; while a complicated program may contain many `.java` source files. Because source files are simple text files, they can be written using any text editor, such as Notepad and Vim.

The following is an example of a very simple Java program.

{% highlight java %}
public class MyProgram {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
{% endhighlight %}

```
Output:
Hello World
```

After the source code is completed, it is compiled by the Java compiler. The purpose of the Java compiler is to take the source code written by the programmer(s) and translated into Java bytecode, which is a machine language that can be understood by the Java Virtual Machine. Java bytecode files have the `**.class**` file extension. During program execution, the Java Virtual Machine reads the bytecode files and execute the instructions. The following figure illustrates the process.

<center><img src="http://docs.oracle.com/javase/tutorial/figures/getStarted/getStarted-compiler.gif"></center>

It's worth noting that because the bytecode is portable, the same `.class` file can be run on different systems.

## What Do I Need

The following basic software are needed to start writing programs in Java.

0. **Java Development Kit**: also know as JDK, this contains Java compiler and JRE.
0. **Text editor**: to write your program

## Installing Java Development Kit

Before writing Java programs, you will need to install Java Runtime Environment (JRE) and Java Development Kit (JDK). Java is an interpreted language; therefore, the JRE will installed a required Java virtual machine (<a href="http://en.wikipedia.org/wiki/Java_virtual_machine" target="_blank">JVM</a>). JDK contains the tools to compile Java programs to the code JVM understands. On some systems, the JDK also contains JRE.

JRE is what you install to run Java programs and applets. JDK is what you install to compile Java programs.

On Windows, the latest version of JRE and JDK can be easily downloaded from the <a href="http://www.oracle.com/technetwork/java/javase/downloads/index.html?ssSourceSiteId=otnjp" target="_blank">Oracle website</a>.

Linux and Mac OS X systems may have Java packaged specifically for that operating system. For example, on Ubuntu, Java can be installed with the following:

```
sudo apt-get install openjdk-7-jre openjdk-7-jdk
```

## Text Editor

In addition to the JDK, you also need a text editor to write your programs. Most systems come with a text editor (such as Notepad on Windows); however, some default editors are not designed for writing programs.

There are many different kind of editors for writing Java programs. The simplest kind is a simple editor without integration with the Java compiler and program runner. There are some really nice editor in this category and include <a href="http://www.sublimetext.com/" target="_blank">Sublime Text</a>, <a href="https://atom.io/" target="_blank">Atom</a>, and <a href="http://macromates.com/" target="_blank">TextMate</a> for Mac OS X.

The second kind of editor integrates the compiler and runner, so you can compile and run your program with a single click. These are called integrated development environments, or IDE. Popular Java IDEs include <a href="http://www.jgrasp.org/" target="_blank">jGrasp</a>, and <a href="https://eclipse.org/" target="_blank">Eclipse</a>.

## Compiling and Running

Now that you have the required software to write a program, let's compile and run the program above. Open up your favorite editor (as mentioned above), and type in (or copy and paste) the very short program above. After that, go ahead and save the file. Note that the file name must match the class name, which is `**MyProgram**`, and ends with `**.java**`.

Now that you have the program saved, we can compile it. If you're using an IDE, there most likely going to be compile button on the toolbar. Here we're demonstrating using the command line. The name of the java compiler that came with JDK is called `javac`. Open your command prompt (or terminal on Linux and Mac OS X), and typing the following command to compile the program.

```
javac HelloWorld.java
```

Note that if you see any error message, make sure you type in the program exactly. If javac cannot find your program, you may have to change your current directory to where you saved your program.

The compiler generated the bytecode of our program `HelloWorld.class` in the current directory. To run the program simply type the following command.

```
java HelloWorld
```

```
Output:
Hello World
```

## Break Down

Though simple, the program above already contain many of the elements of the language. Let's look at some of the elements.

Every piece of Java code is enclosed in a class, which has a name. In this class above, it is named `HelloWorld`, as shown in Line 1. A class is just a way to organize code units in Java. The class also have a visibility of `public`, which means anyone can use this class.

Note: You may give your class any valid name, but in Java convention, class name starts with a capitalized letter.

The `main` method is the entry point of every program, as shown in Line 3. A method, sometimes also known as a function, is a unit of executable code. The method has these components:

0. `public` modifier: which mean anyone can call this method, although `main` is rarely called by other code fragments other than the Java Virtual Machine.
0. `static` modifier: it is not required to create an object of this class before calling this method.
0. `void` return type: this method does not return anything
0. A method parameter: this method has 1 parameter of type an array of strings named args.

Inside the `main` method, there is only one line, which prints out `"Hello World"`. System is a class defined by the Java language. One of the function of this class is the `out` object, which contains method `println()`, which outputs to the screen.

## Summary

- You need JDK to compile and JRE to run Java programs.
- Java program is compiled using `javac`, and ran using `java` command.
- Every piece of Java code is enclosed in a class.
- A program starts execution at the `main()` method.
- `System` is a class in Java SDK that allows keyboard input and screen output.
