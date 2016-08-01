---
layout: post
title: Kth Largest Element
categories: lintcode
tags:
- Java
- Algorithm
- Sort
- Quick Sort
---

Find K-th largest element in an array.

Can you do it in O(n) time and O(1) space?

Example

```
Array              k    Result
[1, 2, 3, 4, 5]    1    5
[9, 3, 2, 4, 8]    2    8
```

The following is a naive O(n log n) time , O(1) space solution.

{% highlight java %}
class Solution {
    /*
     * @param k : description of k
     * @param nums : array of nums, no duplicates
     * @return: description of return
     */
    public int kthLargestElement(int k, int[] nums) {
        Arrays.sort(nums);
        return nums[nums.length - k];
    }
}
{% endhighlight %}