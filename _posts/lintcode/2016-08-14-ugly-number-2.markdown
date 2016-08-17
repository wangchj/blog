---
layout: post
title: Ugly Number II
categories: lintcode
tags:
- Java
- Algorithm
- Priority Queue
---

Ugly number is a number that only have factors `2`, `3` and `5`. Design an algorithm to find the nth ugly number. The first 10 ugly numbers are `1, 2, 3, 4, 5, 6, 8, 9, 10, 12, ...`

Example

```
n    Result
1    1
2    2
9    10
```

{% highlight java %}
class Solution {
    public int nthUglyNumber(int n) {
        PriorityQueue<Long> q = new PriorityQueue<>();
        int count = 0;
        q.add(1L);
        while (true) {
            long head = q.remove();
            count++;
            if (count == n)
                return (int)head;
            long a = head * 2, b = head * 3, c = head * 5;
            if (!q.contains(a)) q.add(a);
            if (!q.contains(b)) q.add(b);
            if (!q.contains(c)) q.add(c);
        }
    }
}
{% endhighlight %}