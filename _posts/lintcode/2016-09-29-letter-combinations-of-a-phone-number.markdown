---
layout: post
title: Letter Combinations of a Phone Number
categories: lintcode
tags:
- Java
- Algorithm
- String
- Backtracking
- Recursion
- Facebook
- Uber
---

Given a string of digits, excluding 0 and 1, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below.

<img src="http://www.lintcode.com/media/problem/200px-Telephone-keypad2.svg.png">

Example

Given `"23"`, return `["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]`

{% highlight java %}
public class Solution {
    
    String[][] letters = {
        {"a", "b", "c"},
        {"d", "e", "f"},
        {"g", "h", "i"},
        {"j", "k", "l"},
        {"m", "n", "o"},
        {"p", "q", "r", "s"},
        {"t", "u", "v"},
        {"w", "x", "y", "z"}
    };
    
    public ArrayList<String> letterCombinations(String digits) {
        return comb(digits, 0);
    }
    
    ArrayList<String> comb(String digits, int index) {
        ArrayList<String> res = new ArrayList<>();
        
        // If digits is empty, just return empty list
        if (digits.length() == 0)
            return res;
            
        String[] letters = getLetters(digits.charAt(index));
        
        // If last digit
        if (index == digits.length() - 1) {
            for (String letter : letters)
                res.add(letter);
            return res;
        }
        
        ArrayList<String> sublist = comb(digits, index + 1);
        
        for (String substr : sublist)
            for (String letter : letters)
                res.add(letter + substr);
        
        return res;
    }
    
    String[] getLetters(char digit) {
        switch (digit) {
            case '2': return letters[0];
            case '3': return letters[1];
            case '4': return letters[2];
            case '5': return letters[3];
            case '6': return letters[4];
            case '7': return letters[5];
            case '8': return letters[6];
            case '9': return letters[7];
        }
        return null;
    }
}
{% endhighlight %}