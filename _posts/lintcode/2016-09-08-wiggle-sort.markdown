---
layout: post
title: Wiggle Sort
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Sort
- Quick Sort
- Google
---

Given an unsorted array `nums`, reorder it in-place such that `nums[0] <= nums[1] >= nums[2] <= nums[3]...`

Example

Given `nums = [3, 5, 2, 1, 6, 4]`, one possible answer is `[1, 6, 2, 5, 3, 4]`.


The following uses shifting approach and the time complexity is O(n<sup>2</sup>).

{% highlight java %}
public class Solution {
    public void wiggleSort(int[] nums) {
        Arrays.sort(nums);
        
        for (int i = 1; i < nums.length; i = i + 2) {
            for (int j = nums.length - 1; j > i; j--) {
                nums[j] ^= nums[j - 1];
                nums[j - 1] ^= nums[j];
                nums[j] ^= nums[j - 1];
            }
        }
    }
}
{% endhighlight %}