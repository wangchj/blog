---
layout: post
status: publish
published: true
title: Valid Parentheses
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1546
wordpress_url: http://codenuggets.com/?p=1546
date: '2016-03-13 01:45:33 -0600'
date_gmt: '2016-03-13 01:45:33 -0600'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- Google
- LintCode easy
- stack
comments: []
---
Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

**Examples**

The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not.

## Solution

This problem can be easily solved by using a stack, as follows:

1. Scan each character of the string from left to right
2. If the current character is `'('`, `'{'`, or `'['`, put it into the stack
3. If the current character is `')'`, `'}'`, or `']'`:
    1. Pop what is on the top of the stack
    2. Compare what is pop and the current character. If they don't match, return false

The Java implementation of the algorithm follows.

{% highlight java %}
public class Solution {
    /**
     * @param s A string
     * @return whether the string is a valid parentheses
     */
    public boolean isValidParentheses(String s) {
        if(s.length() % 2 != 0)
            return false;
            
        Stack<Character> stack = new Stack<Character>();
        for(int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if(c == '{' || c == '(' || c == '[') {
                stack.push(c);
            }
            else {
                if(stack.isEmpty())
                    return false;
                    
                char top = stack.pop();
                if((c == '}' && top != '{') || (c == ')' && top != '(') ||
                    (c == ']' && top != '['))
                    return false;
            }
        }
        return stack.isEmpty();
    }
}
{% endhighlight %}
