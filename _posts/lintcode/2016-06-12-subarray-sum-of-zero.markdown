---
layout: post
title: Subarray Sum of Zero
categories: lintcode
tags:
- Java
- algorithm
- Subarray
- Hash Table
---

Given an integer array, find a subarray where the sum of numbers is zero. Your code should return the index of the first number and the index of the last number.

Example

Given `[-3, 1, 2, -3, 4]`, return `[0, 2]` or `[1, 3]`.

{% highlight java %}
public class Solution {
    /**
     * @param nums: A list of integers
     * @return: A list of integers includes the index of the first number 
     *          and the index of the last number
     */
    public ArrayList<Integer> subarraySum(int[] nums) {
        //A map that maps sum -> index
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        //The list to be returned
        ArrayList<Integer> res = new ArrayList<Integer>();
        //Running sum
        int sum = 0;
        
        for(int i = 0; i < nums.length; i++) {
            sum += nums[i];
            
            //If the sum is 0, we found the zero-sum subarray.
            if(sum == 0) {
                res.add(0);
                res.add(i);
                return res;
            }
            
            //If the current sum is already in the HashMap, that means the
            //subarray between the index we last encountered this sum and
            //i is a zero-sum subarray. Because the sum of this subarray
            //has no effect (0), so we get the same sum.
            if(map.containsKey(sum)) {
                res.add(map.get(sum) + 1);
                res.add(i);
                return res;
            }
            
            //The map does not contain the sum. Add the current sum to the
            //map.
            map.put(sum, i);
        }
        
        return res;
    }
}
{% endhighlight %}