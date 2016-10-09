---
layout: post
title: Longest Consecutive Sequence
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Hash Table
---

Given an unsorted array of integers, find the length of the longest consecutive elements sequence.

Your algorithm should run in O(n) complexity.

Example

```
Input                longest      Return
[1, 3, 2]            [1, 2, 3]    3
[10, 3, 20, 1, 2]    [1, 2, 3]    3
```

The follow uses two hash tables. One maps the start to end of all intervals; and the other maps from end to start.

{% highlight java %}
public class Solution {
    public int longestConsecutive(int[] num) {
        // Map interval start->end
        HashMap<Integer, Integer> stoe = new HashMap<>();
        // Map interval end->start
        HashMap<Integer, Integer> etos = new HashMap<>();
        
        int maxLen = 0;
        int head = 0; // First number of new range
        int tail = 0; // Last number of new range
        
        // For each "i" check if "i" is adjacent to an interval
        for (int i : num) {
            if (stoe.containsKey(i + 1) && etos.containsKey(i - 1)) {
                head = etos.get(i - 1);
                tail = stoe.get(i + 1);
                stoe.put(head, tail);
                stoe.remove(i + 1);
                etos.put(tail, head);
                etos.remove(i - 1);
            }
            else if (stoe.containsKey(i + 1)) {
                head = i;
                tail = stoe.get(i + 1);
                stoe.put(head, tail);
                stoe.remove(i + 1);
                etos.put(tail, head);
            }
            else if (etos.containsKey(i - 1)) {
                head = etos.get(i - 1);
                tail = i;
                stoe.put(head, tail);
                etos.put(tail, head);
                etos.remove(i - 1);
            }
            else {
                stoe.put(i, i);
                etos.put(i, i);
            }
            
            maxLen = Math.max(maxLen, tail - head + 1);
        }
        
        return maxLen;
    }
}
{% endhighlight %}