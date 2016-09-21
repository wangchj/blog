---
layout: post
title: Decode Ways
categories: lintcode
tags:
- Java
- Algorithm
- String
- Dynamic Programming
---

A message containing letters from `A` to `Z` is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```

Given an encoded message containing digits, determine the total number of ways to decode it.

Example

Given encoded message `12`, it could be decoded as `AB` (1, 2) or `L` (12).
The number of ways decoding `12` is `2`.



{% highlight java %}
public class Solution {
    public int numDecodings(String s) {
        return ways(s, 0, new HashMap<Integer, Integer>());
    }
    
     /**
     * Recursive search using DP (map).
     */
    public static int ways(String s, int start, HashMap<Integer, Integer> map)
    {
        if(s == null || s.length() == 0 || s.charAt(start) == '0' || start >= s.length())
            return 0;
        if(start == s.length() - 1)
            return 1;
        if(map.containsKey(start))
            return map.get(start);
        
        //Take one character
        int one = ways(s, start + 1, map);
        
        //Take two characters
        int i = Integer.valueOf(s.substring(start, start + 2));
        int two = 0;
        if(i > 0 && i < 27)
        {
            if(start == s.length() - 2)
                two = 1;
            else
                two = ways(s, start + 2, map);
        }
        
        map.put(start, one + two);
        return one + two;
    }
}
{% endhighlight %}