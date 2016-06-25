---
layout: post
title: Intersection of Two Arrays II
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Hash Table
---

Given two arrays, write a function to compute their intersection. An element in the result array can have duplicates, but the duplicate should appear as many times as in both arrays. The result array can be in any order.


Example

```
Array 1         Array 2      Intersection
[]              [1, 2]       []
[1, 2, 3, 4]    [3, 4]       [3, 4]
[1, 2, 2, 1]    [1, 1, 2]    [1, 1, 2]
```

{% highlight java %}
public class Solution {
    /**
     * @param nums1 an integer array
     * @param nums2 an integer array
     * @return an integer array
     */
    public int[] intersection(int[] nums1, int[] nums2) {
        if (nums1.length == 0 || nums2.length == 0)
            return new int[0];
            
        HashMap<Integer, Integer> count = new HashMap<>();
        int[] res = new int[nums1.length + nums2.length];
        int i = 0;
        
        for (int e : nums1) {
            if (count.containsKey(e))
                count.put(e, count.get(e) + 1);
            else
                count.put(e, 1);
        }
        for (int e : nums2) {
            if (count.containsKey(e) && count.get(e) != 0) {
                res[i] = e;
                count.put(e, count.get(e) - 1);
                i++;
            }    
        }
        
        return Arrays.copyOf(res, i);
    }
}
{% endhighlight %}