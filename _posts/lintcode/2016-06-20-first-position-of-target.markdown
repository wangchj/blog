---
layout: post
title: First Position of Target
categories: lintcode
tags:
- Java
- Algorithm
- Binary Search
- Array
---

For a given sorted array (ascending order) and a target number, find the first index of this number in `O(log n)` time complexity. If the target number does not exist in the array, return `-1`.

Example

If the array is `[1, 2, 3, 3, 4, 5, 10]`, for given target `3`, return `2`.

Challenge: If the count of numbers is bigger than 2<sup>32</sup>, can your code work properly?

{% highlight java %}
class Solution {
    /**
     * @param nums: The integer array.
     * @param target: Target to find.
     * @return: The first position of target. Position starts from 0.
     */
    public int binarySearch(int[] nums, int target) {
        if(nums == null || nums.length == 0)
            return -1;
            
        int left = 0;
        int right = nums.length - 1;
        while(left <= right) {
            int mid = (right - left) / 2 + left;
            if(nums[mid] == target) {
                if(mid == 0)
                    return mid;
                if(nums[mid] != nums[mid - 1])
                    return mid;
                if(nums[mid] == nums[mid - 1])
                    right = mid - 1;
            }
            else {
                if(nums[mid] < target)
                    left = mid + 1;
                else //nums[mid] > target
                    right = mid - 1;
            }
        }
        
        return -1;
    }
}
{% endhighlight %}