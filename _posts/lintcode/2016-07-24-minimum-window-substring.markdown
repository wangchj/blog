---
layout: post
title: Minimum Window Substring
categories: lintcode
tags:
- Java
- Algorithm
- Hash Table
- LinkedIn
- Facebook
---

Given a string source and a string target, find the minimum window in source which will contain all the characters in target.

If there is no such window in source that covers all characters in target, return the emtpy string "".

If there are multiple such windows, you are guaranteed that there will always be only one unique minimum window in source.

Challenge: time complexity of O(n).

Example

```
Source     target    Solution
abc        a         a
abc        ac        abc
abcd       ac        abc
abcdecf    acc       abcdec
```

{% highlight java %}
public class Solution {
    /**
     * @param source: A string
     * @param target: A string
     * @return: A string denote the minimum window
     *          Return "" if there is no such a string
     */
    public String minWindow(String source, String target) {
        if (source == null || source == "")
            return "";
        
        String res = null;
        
        HashMap<Character, Integer> t = new HashMap<>();
        for (int i = 0; i < target.length(); i++) {
            char c = target.charAt(i);
            if (t.containsKey(c))
                t.put(c, t.get(c) + 1);
            else
                t.put(c, 1);
        }
        
        for (int i = 0; i <= source.length() - target.length(); i++) {
            HashMap<Character, Integer> m = (HashMap)t.clone();
            for (int j = i; j < source.length(); j++) {
                char c = source.charAt(j);
                if (m.containsKey(c)) {
                    if (m.get(c) == 1)
                        m.remove(c);
                    else
                        m.put(c, m.get(c) - 1);
                        
                    if (m.size() == 0) {
                        if (res == null || j + 1 - i < res.length())
                            res = source.substring(i, j + 1);
                        break;
                    }
                }
            }
        }
        
        return res == null ? "" : res;
    }
}
{% endhighlight %}