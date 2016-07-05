---
layout: post
title: Intersection of Two Arrays
categories: lintcode
tags:
- Java
- Algorithm
- Set
- Hash Table
- Hash Set
---

Given two arrays, representing sets, write a function to compute the intersection of these two sets. Each element in the result must be unique and the result can be in any order.


Example

```
Array 1         Array 2      Intersection
[]              [1, 2]       []
[1, 2, 3, 4]    [3, 4]       [3, 4]
[1, 2, 2, 1]    [1, 2, 2]    [1, 2]
[1, 2, 3, 4]    [5, 6]       []
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
            
        Set<Integer> s = new HashSet<>();
        Set<Integer> r = new HashSet<>();
        int[] res = new int[nums1.length + nums2.length];
        int i = 0;
        
        for (int e : nums1)
            s.add(e);
        for (int e : nums2) {
            if (s.contains(e) && !r.contains(e)) {
                r.add(e);
                res[i] = e;
                i++;
            }    
        }
        
        return Arrays.copyOf(res, i);
    }
}
{% endhighlight %}