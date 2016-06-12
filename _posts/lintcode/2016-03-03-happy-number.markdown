---
layout: post
status: publish
published: true
title: Happy Number
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1497
wordpress_url: http://codenuggets.com/?p=1497
date: '2016-03-03 03:19:36 -0600'
date_gmt: '2016-03-03 03:19:36 -0600'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- Hashtable
- HashSet
- Mathematics
comments: []
---

Write an algorithm to determine if a number is happy.

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

**Example**

19 is a happy number

```
1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1
```

## Solution Discussion

According to the Wikipedia entry [Happy Number](https://en.wikipedia.org/wiki/Happy_number), an non-happy number will eventually reach the sequence `4, 16, 37, 58, 89, 145, 42, 20, 4,...` and loop in this sequence forever.

In our solution, we just have to check if the current square sum has already been considered. If the sum has already been considered, then we're in a loop and the current number is not a happy number. We check this look a `HashSet<Integer>`. For each sum we have considered for the number `n`, we add the sum to the hash set. When we compute a new sum, we check the hash set to see if the sum is already in the set; if it is, we immediately return `false`. If the sum reaches `1`, we return `true`.

The code of this solution follows.

{% highlight java %}
public class Solution {
    /**
     * @param n an integer
     * @return true if this is a happy number or false
     */
    public boolean isHappy(int n) {
        if(n == 1)
            return true;
        
        //A set to store values already considered.
        HashSet<Integer> set = new HashSet<Integer>();
        
        while(true) {
            //Get the digits
            String digits = "" + n;
            //Sum of square of digits
            int sum = 0;
            
            for(int i = 0; i < digits.length(); i++) {
                int d = Character.getNumericValue(digits.charAt(i));
                sum += d * d;
            }
            
            //Sum already considered
            if(set.contains(sum))
                return false;
            
            //Sum hasn't been considered
            
            //If it's a single digit number
            if(sum == 1)
                return true;
            
            //If it's not a single digit number
            set.add(sum);
            n = sum;
        }
    }
}
{% endhighlight %}