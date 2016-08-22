---
layout: post
title: Valid Palindrome
categories: lintcode
tags:
- Java
- Algorithm
- String
- Two Pointers
- Facebook
- Zenefits
- Uber
- Equifax
---

A palindrome is a word, phrase, number, or other sequence of characters which reads the same backward or forward. Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

Example

`"Do geese see God?"` is a palindrome.

`"A man, a plan, a canal: Panama"` is a palindrome.

`"race a car"` is not a palindrome.

{% highlight java %}
public class Solution {
    public boolean isPalindrome(String s) {
        if(s == null || s.isEmpty())
            return true;
            
        s = s.toLowerCase();
        
        int i = 0, j = s.length() - 1;
        while(i < j) {
            if(!isValidChar(s.charAt(i))) {
                i++;
            }
            else if(!isValidChar(s.charAt(j))) {
                j--;
            }
            else if(s.charAt(i) != s.charAt(j)) {
                return false;
            }
            else {
                i++;
                j--;
            }
        }
        return true;
    }
    
    private boolean isValidChar(char c) {
        if((c >= '0' && c <= '9') || (c >= 'A' && c <= 'Z') ||
            (c >= 'a' && c <= 'z'))
            return true;
        return false;
    }
}
{% endhighlight %}