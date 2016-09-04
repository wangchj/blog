---
layout: post
title: Restore IP Addresses
categories: lintcode
tags:
- Java
- Algorithm
- String
- Depth First Search
- Backtracking
- Recursion
---

Given a string containing only digits, restore it by returning all possible valid IP address combinations. Order of the result does not matter.

Example

```
Given "25525511135", return:

[
    "255.255.11.135",
    "255.255.111.35"
]
```

The following uses depth-first search.

{% highlight java %}
public class Solution {
    /**
     * @param s the IP string
     * @return All possible valid IP addresses
     */
    public ArrayList<String> restoreIpAddresses(String s) {
        ArrayList<String> result = new ArrayList<String>();
        restore(s, 0, new ArrayList<String>(), result);
        return result;
    }
    
    public void restore(String s, int start, ArrayList<String> path, ArrayList<String> result)
    {
        //If already have 4 components, but haven't reached end,
        //Or components < 4, but reached end.
        if((path.size() == 4 && start < s.length()) || (path.size() < 4 && start >= s.length()))
            return;
        if(path.size() == 4 && start >= s.length())
        {
            result.add(makeIp(path));
            return;
        }
        
        //Eat one char
        path.add(s.substring(start, start + 1));
        restore(s, start + 1, path, result);
        path.remove(path.size() - 1);
        
        //Eat two chars
        if(start + 2 <= s.length())
        {
            String sub = s.substring(start, start + 2);
            if(sub.charAt(0) != '0')
            {
                path.add(sub);
                restore(s, start + 2, path, result);
                path.remove(path.size() - 1);
            }
        }
        
        //Eat three chars
        if(start + 3 <= s.length())
        {
            String sub = s.substring(start, start + 3);
            int i = Integer.valueOf(sub);
            if(sub.charAt(0) != '0' && i >= 0 && i <= 255)
            {
                path.add(sub);
                restore(s, start + 3, path, result);
                path.remove(path.size() - 1);
            }
        } 
    }
    
    public String makeIp(ArrayList<String> path)
    {
        StringBuilder r = new StringBuilder();
        for(String s : path)
        {
            r.append(s);
            if(s != path.get(path.size() - 1))
                r.append('.');
        }
        return r.toString();
    }
}
{% endhighlight %}