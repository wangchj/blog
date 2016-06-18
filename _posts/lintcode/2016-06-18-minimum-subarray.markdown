---
layout: post
title: Minimum Subarray
categories: lintcode
tags:
- Java
- Algorithm
- Greedy
- Array
- Subarray
---

Given an array of integers, find the subarray with smallest sum and return the sum. The subarray should contain at least one element from the array.

Example

```
A = [1, -1, -2, 1]  =>  Min sum = -3
```

{% highlight java %}
public class Solution {
    /**
     * @param nums: a list of integers
     * @return: A integer indicate the sum of minimum subarray
     */
    public int minSubArray(ArrayList<Integer> nums) {
        if(nums == null || nums.isEmpty())
            return 0;
            
        int min = nums.get(0);
        int sum = nums.get(0);
        
        for(int i = 1; i < nums.size(); i++) {
            int curr = nums.get(i);
            if(curr < sum + curr)
                sum = curr;
            else
                sum += curr;
            if(sum < min)
                min = sum;
        }
        
        return min;
    }
}
{% endhighlight %}