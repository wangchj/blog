---
layout: post
title: Flatten List
categories: lintcode
tags:
- Java
- Algorithm
- Recursion
---

Given a list, each element in the list can be a list or integer. flatten it into a simply list with integers.

If the element in the given list is a list, it can contain list too.

Example

```
Input              Output
[1, 2, [1, 2]]     [1,2,1,2]
[4,[3,[2,[1]]]]    [4,3,2,1]
```

Recursive algorithm.

{% highlight java %}
public class Solution {
    public List<Integer> flatten(List<NestedInteger> nestedList) {
        List<Integer> res = new ArrayList<>();
        flatten(nestedList, res);
        return res;
    }
    
    void flatten(List<NestedInteger> list, List<Integer> res) {
        if (list.size() == 0)
            return;
        for (NestedInteger i : list) {
            if (i.isInteger())
                res.add(i.getInteger());
            else
                flatten(i.getList(), res);
        }
    }
}
{% endhighlight %}

{% highlight java %}
public interface NestedInteger {
    // @return true if this NestedInteger holds a single integer,
    // rather than a nested list.
    public boolean isInteger();

    // @return the single integer that this NestedInteger holds,
    // if it holds a single integer
    // Return null if this NestedInteger holds a nested list
    public Integer getInteger();

    // @return the nested list that this NestedInteger holds,
    // if it holds a nested list
    // Return null if this NestedInteger holds a single integer
    public List<NestedInteger> getList();
}
{% endhighlight %}