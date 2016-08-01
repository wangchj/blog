---
layout: post
title: Permutation
categories: lintcode
tags:
- Java
- Algorithm
- Recursion
- LinkedIn
---

Given a list of numbers, return all possible permutations.

Example

For `nums = [1,2,3]`, the permutations are:

```
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

Recursive solution:

{% highlight java %}
class Solution {
    /**
     * @param nums: A list of integers.
     * @return: A list of permutations.
     */
    public ArrayList<ArrayList<Integer>> permute(ArrayList<Integer> nums) {
        ArrayList<ArrayList<Integer>> res = new ArrayList<ArrayList<Integer>>();
        
        if(nums == null || nums.size() == 0)
            return res;
            
        if(nums.size() == 1)
        {
            ArrayList<Integer> l = new ArrayList<Integer>();
            l.add(nums.get(0));
            res.add(l);
            return res;
        }
            
        //Take the first element of the array
        int head = nums.get(0);
        //Remainder list
        nums.remove(0);
        //Make recursive call
        ArrayList<ArrayList<Integer>> perms = permute(nums);
        
        for(ArrayList<Integer> perm : perms)
        {
            for(int i = 0; i <= perm.size(); i++)
            {
                ArrayList<Integer> l = new ArrayList<Integer>(perm);
                l.add(i, head);
                res.add(l);
            }
        }
        
        return res;
    }
}
{% endhighlight %}