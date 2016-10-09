---
layout: post
title: Simplify Path
categories: lintcode
tags:
- Java
- Algorithm
- String
- Stack
---

Given an absolute path for a file (Unix-style), simplify it.

The rules for a path follows:

1. The symbol `.` indicates the current location. For example, `/a/./` can be simplied to `/a/`.
2. The symbol `..` indicates the parent location. For example, `/a/b/../` can be simplied to `/a/`.
3. Multiple slashes can be ignore. For example,  `/home//foo` ca be simplified to `/home/foo`.

Example

```
Path             Return
/..              /
/home/           /home
/home/./user     /home/user
/home/../user    /user
/home//user      /home/user
```

{% highlight java %}
public class Solution {
    public String simplifyPath(String path) {
        String[] tokens = path.split("/");
        Stack<String> stack = new Stack<>();
        
        for (String token : tokens) {
            if (token.equals("") || token.equals("."))
                continue;
            if (token.equals("..")) {
                if (!stack.isEmpty())
                    stack.pop();
            }
            else
                stack.push(token);
        }
        
        StringBuilder res = new StringBuilder();
        
        for (String token : stack) {
            res.append('/');
            res.append(token);
        }
        
        return res.length() == 0 ? "/" : res.toString();
    }
}
{% endhighlight %}