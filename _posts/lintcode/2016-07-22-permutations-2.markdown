---
layout: post
title: Permutations II
categories: lintcode
tags:
- Java
- Algorithm
- Recursion
- Depth First Search
- LinkedIn
---

Given a list of numbers with duplicate number in it. Find all unique permutations.

Example

For numbers `[1,2,2]` the unique permutations are:

```
[
  [1,2,2],
  [2,1,2],
  [2,2,1]
]
```

Recursive solution:

{% highlight java %}
class Solution {
    /**
     * @param nums: A list of integers.
     * @return: A list of unique permutations.
     */
    public ArrayList<ArrayList<Integer>> permuteUnique(ArrayList<Integer> nums)
    {
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
        ArrayList<ArrayList<Integer>> perms = permuteUnique(nums);
        
        for(ArrayList<Integer> perm : perms)
        {
            for(int i = 0; i <= perm.size(); i++)
            {
                ArrayList<Integer> l = new ArrayList<Integer>(perm);
                l.add(i, head);
                if (!res.contains(l))
                    res.add(l);
            }
        }
        
        return res;
    }
}
{% endhighlight %}