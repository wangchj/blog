---
layout: post
status: publish
published: true
title: Java Arithmetic Operators
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1137
wordpress_url: http://codenuggets.com/?p=1137
date: '2014-11-10 20:22:36 -0600'
date_gmt: '2014-11-10 20:22:36 -0600'
categories:
- Programming
- Java
tags: []
comments:
- id: 4114
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2014-12-27 22:01:28 -0600'
  date_gmt: '2014-12-27 22:01:28 -0600'
  content: "[&#8230;] Step Java Program Basic Structure Java Data and Data Types Java
    Classes and Objects Java Arithmetic Operators Java Data and Data Types 2 Java
    Boolean Expressions Java [&#8230;]"
---
In this article we are going to cover an easy topics of arithmetic operators and expressions in Java. Arithmetic is the basic calculation of numbers using operators (like addition and subtraction). An arithmetic expression is a mathematical formula that can be evaluated to numeric value and consists of operands (numbers and variables) and operators.

An arithmetic expression can be very simple and contains only a number or can be very complex that contains many operands and operations. The following shows a lists of examples of expressions. We are assigning the result of the expressions to a variable named `result`; however, the right hand side of the equation is what we mean by expression.

{% highlight java %}
result = 2;                 //2 is a valid expression
result = 1 + 2;             //Another simple expression
result = (1 + 2) * (2 + 3); //Expressions can contain parentheses 
{% endhighlight %}

## Operators and Order of Operation

The following table lists Java's arithmetic operators along with the precedence of operation. Java has a very powerful expression evaluation system and follows the traditional order of evaluation: expression are evaluated from left to right; expressions in parentheses are evaluated first; and multiplications and divisions comes before additions and subtractions.

<table>
<colgroup>
<col style="text-align:middle">
<col align="middle">
    </colgroup>
<tr>
<th>Precedence</th>
<th>Operator</th>
<th></th>
</tr>
<tr>
<td style="text-align:center">1</td>
<td style="text-align:center">( )</td>
<td>parentheses</td>
</tr>
<tr>
<td style="text-align:center">2</td>
<td style="text-align:center">-</td>
<td>negation</td>
</tr>
<tr>
<td rowspan="3" style="text-align:center">3</td>
<td style="text-align:center">*</td>
<td>multiplication</td>
</tr>
<tr>
<td style="text-align:center">/</td>
<td>division</td>
</tr>
<tr>
<td style="text-align:center">%</td>
<td>modulus (division remainder)</td>
</tr>
<tr>
<td rowspan="2" style="text-align:center">4</td>
<td style="text-align:center">+</td>
<td>addition</td>
</tr>
<tr>
<td style="text-align:center">-</td>
<td>subtraction</td>
</tr>
<tr>
<td style="text-align:center">5</td>
<td style="text-align:center">=</td>
<td>assignment</td>
</tr>
</table>
Operator with lower precedence value is evaluated first.

Note that Java does not have the exponentiation operator; however, exponentiation can be accomplished using the `Math.pow()` method of Java's standard library.

Most of the operators are self-explanatory. Here we give a few examples of the operators (and the result of evaluation).

{% highlight java %}
public class ExpressionExample {
    public static void main(String[] args) {
        int result = 0;
        result = -1;     //Negation operator, result = -1
        result = -1 + 2; //result = 1
        result = 3 % 2;  //The remainder of 3 / 2; result = 1
        result = 2 % 2;  //The remainder of 2 / 2; result = 0
        
        int a = 5;
        result = a * a;  //result = 5 * 5 = 25
    }
}
{% endhighlight %}

## Shorthand Operators

In addition to the operator presented in the previous, Java also supports increment and decrement operators (shown in table below). These operators are used to add or subtract an integer variable by 1.

<table>
<tr>
<th>Operator</th>
<th>Operation</th>
<th style="text-align:left">Effect</th>
</tr>
<tr>
<td style="text-align:center">++</td>
<td style="text-align:center">increment</td>
<td>Add 1 to a variable</td>
</tr>
<tr>
<td style="text-align:center">- -</td>
<td style="text-align:center">decrement</td>
<td>substract 1 from a variable</td>
</tr>
</table>
These operators can be applied before (prefix) or after (postfix) a variable. Examples are below.

{% highlight java %}
public class IncrementDecrementOperators {
    public static void main(String[] args) {
        int count = 0;
        count++;         //count is now 1
        count++;         //count is now 2
        count--;         //count is now 1
        
        int a = count++; //postfix: a = 1, count = 2
        int b = ++count; //preix  : b = 3, count = 3
    }
}
{% endhighlight %}

We can apply a shorthand assignment operator to a variable. These are form by combing an operator with the assignment operator. The effect of this is that the operation is performed to the variable, then the result is assigned to the same variable. The following code shows examples.

{% highlight java %}
public class AssigmentOperators {
    public static void main(String[] args) {
        int count = 0;
        count += 5;     //count = count + 5 --> count = 5
        count *= 2;     //count = count * 2 --> count = 10
    }
}
{% endhighlight %}

## About Data Types

Every operand of a operation has a type. For example when we have expression `2 + 3`, both `2` and `3` has an implicit type of `int`. Of course when a variable is used in an expression, the type of the variable is the operand's type. Implicit types depend on the literal.

When both operands are the same type, there is no type conversion; and the result data type is also the same type. When operands are different type, Java implicitly converts one operand to the other type, then performs the operation. This is called **numeric promotion**, where a narrower type is promoted to a larger type.

Sometime this gives unexpected result. Consider the following example. We expect the value of `result` to be `0.5`; however, if you run the program, you would see that the program outputs `0.0`! This is because both operands are integers, so the operation is actually an integer division, which produces 0, then converted to a `float` by the assignment operator.

{% highlight java %}
public class IntegerDivision {
    public static void main(String[] args) {
        float result = 2 / 4;
        System.out.println(result);  //Output: 0.0
    }
}
{% endhighlight %}

There is also the issue of data conversion discussed in the article Data Types. The following code gives the error `"incompatible types: double found where float required"`.

{% highlight java %}
public class NarrowConversionError {
    public static void main(String[] args) {
        float result = 2.0 / 4.0;   //Error
    }
}
{% endhighlight %}

The reason for this error is that `2.0` and `4.0` are implicitly of type `double`. The result, also a `double`, is then to be converted to a `float`. This conversion is a narrowing conversion, which causes an error.

To remedy the error, it is better to avoid narrowing conversion, such that declare the variable as `double`. The other approach is to force the result to a `float` using a cast, as shown below.

{% highlight java %}
public class TypeCasting {
    public static void main(String[] args) {
        float result = (float)(2.0 / 4.0);   //Type casting
    }
}
{% endhighlight %}