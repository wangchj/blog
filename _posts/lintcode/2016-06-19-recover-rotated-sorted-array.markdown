---
layout: post
title: Recover Rotated Sorted Array
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Sorted Array
---

Given a rotated sorted array, recover it to sorted array in-place. A rotated array is an array in which its elements are shifted. For example, `[3, 4, 1, 2]` is a rotated array of array `[1, 2, 3, 4]` by 2 places.

Example

```
[4, 5, 1, 2, 3] -> [1, 2, 3, 4, 5]
```

The algorithm should run in-place with O(1) space and O(n) time.

{% highlight java %}
public class Solution {
    /**
     * We first find the index of the minimum element. If there are no
     * duplicates, we can use binary search; however, that is not the case here.
     * @param nums: The rotated sorted array
     * @return: void
     */
    public void recoverRotatedSortedArray(ArrayList<Integer> nums) {
        int min = nums.get(0);
        int minIndex = 0;
        
        for(int i = 1; i < nums.size() - 1; i++) {
            int curr = nums.get(i);
            if(curr < min) {
                min = curr;
                minIndex = i;
            }
        }
        
        if(minIndex == 0)
            return;
            
        if(minIndex <= nums.size() / 2) {
            for(int i = 0; i < minIndex; i++) {
                nums.add(nums.remove(0));
            }
        }
        else {
            for(int i = 0; i < nums.size() - minIndex; i++) {
                nums.add(0, nums.remove(nums.size() - 1));
            }
        }
    }
}
{% endhighlight %}