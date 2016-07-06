---
layout: post
title: Generate Parentheses
categories: lintcode
tags:
- Java
- Algorithm
- Recursion
- Backtracking
- String
- Catalan number
- Zenefits
- Google
---

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

Example

```
n    result
1    ()
2    (()), ()()
3    ((())), (()()), (())(), ()(()), ()()()
```

{% highlight java %}
public class Solution {
    /**
     * @param n n pairs
     * @return All combinations of well-formed parentheses
     */
    public ArrayList<String> generateParenthesis(int n) {
        ArrayList<String> res = new ArrayList<String>();
        
        if(n == 0) {
            res.add("");
            return res;
        }
        if(n == 1) {
            res.add("()");
            return res;
        }
        
        for(int i = 0; i < n; i++) {
            ArrayList<String> a = generateParenthesis(i);
            ArrayList<String> b = generateParenthesis(n - 1 - i);
            
            for(String s1 : a)
                for(String s2 : b)
                    res.add('(' + s1 + ')' + s2);
        }
        return res;
    }
}
{% endhighlight %}