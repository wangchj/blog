---
layout: post
title: Evaluate Reverse Polish Notation
categories: lintcode
tags:
- Java
- Algorithm
- Stack
- LinkedIn
---

Evaluate the value of an arithmetic expression in Reverse Polish Notation.

Valid operators are `+`, `-`, `*`, `/`. Each operand may be an integer or another expression.

For more information, please see [reversed polish notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation).

Example

```
Input                         Equivalent        Result
["2", "1", "+", "3", "*"]     ((2 + 1) * 3)     9
["4", "13", "5", "/", "+"]    (4 + (13 / 5))    6
```

{% highlight java %}
public class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<Integer>();
        for(int i = 0; i < tokens.length; i++)
        {
            if(tokens[i].length() > 1 || Character.isDigit(tokens[i].charAt(0)))
                stack.push(Integer.parseInt(tokens[i]));
            else
            {
                int b = stack.pop();
                int a = stack.pop();
                int r = 0;
                switch(tokens[i])
                {
                    case "+":
                        r = a + b; break;
                    case "-":
                        r = a - b; break;
                    case "*":
                        r = a * b; break;
                    case "/":
                        r = (int)(a / b); break;
                }
                stack.push(r);
            }
        }
        return stack.pop();
    }
}
{% endhighlight %}
