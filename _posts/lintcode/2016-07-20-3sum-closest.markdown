---
layout: post
title: 3Sum Closest
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Sort
- Two Pointers
---

Given an array `S` of `n` integers, find three integers in `S` such that the sum is closest to a given number, `target`. Return the sum of the three integers. You may assume that each input would have exactly one solution.

Example

```
Array             Target    Solutions
[-1, 2, 1, -4]    1         2 (-1 + 2 + 1 = 2)
[1, 2, 3, 4]      10        9 (2 + 3 + 4 = 9)
```

Naive O(n<sup>3</sup>) solution:

{% highlight java %}
public class Solution {
    /**
     * @param numbers: Give an array numbers of n integer
     * @param target : An integer
     * @return : return the sum of the three integers, the sum closest target.
     */
    public int threeSumClosest(int[] numbers, int target) {
        int res = 0, md = Integer.MAX_VALUE; 
        for (int i = 0; i < numbers.length - 2; i++) {
            for (int j = i + 1; j < numbers.length - 1; j++) {
                for (int k = j + 1; k < numbers.length; k++) {
                    int s = numbers[i] + numbers[j] + numbers[k];
                    int d = Math.abs(target - s);
                    if (d == 0)
                        return s;
                    if (d < md) {
                        res = s;
                        md = d;
                    }
                }
            }
        }
        return res;
    }
}
{% endhighlight %}

Better O(n<sup>2</sup>) solution:

{% highlight java %}
public class Solution {
    /**
     * @param numbers: Give an array numbers of n integer
     * @param target : An integer
     * @return : return the sum of the three integers, the sum closest target.
     */
    public int threeSumClosest(int[] numbers, int target) {
        int res = 0, minDif = Integer.MAX_VALUE;
        Arrays.sort(numbers);
        for (int i = 0; i < numbers.length - 2; i++) {
            int j = i + 1;
            int k = numbers.length - 1;
            while (j < k) {
                int sum = number[i] + numbers[j] + numbers[k];
                int dif = Math.abs(target - sum);
                
                if (dif == 0)
                    return sum;
                
                if (dif < minDif) {
                    res = sum;
                    minDif = dif;
                }
                
                if (sum < target)
                    j++;
                else
                    k--;
            }
        }
        return res;
    }
}
{% endhighlight %}