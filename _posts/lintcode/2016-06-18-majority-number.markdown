---
layout: post
title: Majority Number
categories: lintcode
tags:
- Java
- Algorithm
- Greedy
- Enumeration
- Zenefits
---

Given an array of integers, the majority number is the number that occurs more than half of the size of the array. Find the number with O(n) time and O(1) space.

Example

Given `[1, 1, 1, 1, 2, 2, 2]`, return `1`

{% highlight java %}
public class Solution {
    /**
     * @param nums: a list of integers
     * @return: find a  majority number
     */
    public int majorityNumber(ArrayList<Integer> nums) {
        int candidate = nums.get(0);
        int vote = 1;
        
        for(int i = 1; i < nums.size(); i++) {
            if(nums.get(i) == candidate) {
                vote++;
            }
            else {
                vote--;
                if(vote == 0) {
                    candidate = nums.get(i);
                    vote = 1;
                }
            }
        }
        
        vote = 0;
        for(int i = 0; i < nums.size(); i++) {
            if(nums.get(i) == candidate)
                vote++;
        }
        
        if(vote > nums.size() / 2)
            return candidate;
        else
            return -1;
    }
}
{% endhighlight %}