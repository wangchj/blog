---
layout: post
title: Compare Strings
categories: lintcode
tags:
- Java
- algorithm
- String
- LintCode Copyright
---

Compare two strings `A` and `B`, determine whether `A` contains all of the characters in `B`. The characters in string `A` and `B` are all upper case letters. The characters of `B` in `A` are not necessary continuous or ordered.

Example

For `A = "ABCD"`, `B = "ACD"`, return `true`.  
For `A = "ABCD"`, `B = "AABC"`, return `false`.

{% highlight java %}
public class Solution {
    /**
     * @param A : A string includes Upper Case letters
     * @param B : A string includes Upper Case letter
     * @return :  if string A contains all of the characters in B return true else return false
     */
    public boolean compareStrings(String A, String B) {
        if((A == null && B == null) || (A.isEmpty() && B.isEmpty()))
            return true;
        if(A.length() < B.length())
            return false;
            
        int[] countA = new int[26];
        int[] countB = new int[26];
        
        for(int i = 0; i < A.length(); i++) {
            char c = A.charAt(i);
            countA[c - 'A']++;
        }
        
        for(int i = 0; i < B.length(); i++) {
            char c = B.charAt(i);
            int j = c - 'A';
            countB[j]++;
            if(countB[j] > countA[j])
                return false;
        }
        
        return true;
    }
}
{% endhighlight %}