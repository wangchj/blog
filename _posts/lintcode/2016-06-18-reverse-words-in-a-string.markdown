---
layout: post
title: Reverse Words in a String
categories: lintcode
tags:
- Java
- algorithm
- String
---

Given an input string, reverse the string word by word.

Example

Given `s = "the sky is blue"`,

return `"blue is sky the"`.

Clarification

- What constitutes a word?
  A sequence of non-space characters constitutes a word.
- Could the input string contain leading or trailing spaces?
  Yes. However, your reversed string should not contain leading or trailing spaces.
- How about multiple spaces between two words?
  Reduce them to a single space in the reversed string.

{% highlight java %}
public class Solution {
    /**
     * @param s : A string
     * @return : A string
     */
    public String reverseWords(String s) {
        if(s == null || s.isEmpty())
            return s;
        StringBuilder res = new StringBuilder();
        int rear = s.length() - 1;
        int front = 0;
        
        while(rear >= 0) {
            //Find rear index
            while(rear >= 0 && s.charAt(rear) == ' ') {
                rear--;
            }
            
            //If no more words, end the loop
            if(rear < 0)
                break;
                
            //Find front index
            front = rear;
            while(front >= 0 && s.charAt(front) != ' ') {
                front--;
            }
            
            //Add the word within [front, rear] to the result
            if(res.length() != 0)
                res.append(' ');
            res.append(s.substring(front + 1, rear + 1));
            
            rear = front - 1;
        }
        
        return res.toString();
    }
}
{% endhighlight %}