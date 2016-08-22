---
layout: post
title: Singleton
categories: lintcode
tags:
- Java
- Algorithm
- Object Oriented Design
---

Singleton is a most widely used design pattern. If a class has and only has one instance at every moment, we call this design as singleton. For example, for class Mouse (not a animal mouse), we should design it in singleton.

You job is to implement a `getInstance()` method for given class, return the same instance of this class every time you call this method.

Example

```
A a = A.getInstance();
A b = A.getInstance();
a == b  // returns true
```

{% highlight java %}
class Solution {
    private static Solution instance;

    public static Solution getInstance() {
        if(instance == null)
            instance = new Solution();
        return instance;
    }
}
{% endhighlight %}