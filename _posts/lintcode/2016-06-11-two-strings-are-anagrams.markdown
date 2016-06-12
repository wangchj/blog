---
layout: post
title: Two Strings Are Anagrams
categories: lintcode
tags:
- Java
- algorithm
- String
- Cracking The Coding Interview
---

Write a method `anagram(s,t)` to decide if two strings are anagrams. Two strings are anagrams if they have the same letters in different order.

Example

```
"abcd"  "dcab"  ->  anagrams
"ab"    "ab"    ->  anagrams
"ab"    "ac"    ->  not anagrams
```

Is it possible to achieve O(1) extra space?


{% highlight java %}
public class Solution {
    /**
     * @param s: The first string
     * @param t: The second string
     * @return true or false
     */
    public boolean anagram(String s, String t) {
        if(s.length() != t.length())
            return false;
        HashMap<Character, Integer> map = new HashMap<Character, Integer>();
        for(int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if(map.containsKey(c)) {
                map.put(c, map.get(c) + 1);
            }
            else {
                map.put(c, 1);
            }
        }
        
        for(int i = 0; i < t.length(); i++) {
            char c = t.charAt(i);
            if(map.containsKey(c)) {
                if(map.get(c) == 0)
                    return false;
                else
                    map.put(c, map.get(c) - 1);
            }
            else {
                return false;
            }
        }
        
        return true;
    }
}
{% endhighlight %}