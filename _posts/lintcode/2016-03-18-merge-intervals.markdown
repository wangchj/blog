---
layout: post
status: publish
published: true
title: Merge Intervals
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1561
wordpress_url: http://codenuggets.com/?p=1561
date: '2016-03-18 03:45:50 -0500'
date_gmt: '2016-03-18 03:45:50 -0500'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- Google
- LintCode easy
- array
- Comparator
- sort
- LinkedIn
comments: []
---
Given a collection of intervals, merge all overlapping intervals.

Example:

Given intervals => merged intervals:

```
[                     [
  [1, 3],               [1, 6],
  [2, 6],      =>       [8, 10],
  [8, 10],              [15, 18]
  [15, 18]            ]
]
```

## Solution

One simple solution is to compare each interval with every other interval in the list, and merge any overlapping intervals. However, the time complexity of this algorithm is O(n<sup>2</sup>), where n is the number of intervals.

A better algorithm follows:

1. Sort the list of intervals, based on the start time of each interval.
2. Perform linear scan and merge any overlapping adjacent intervals.

Because we have to sort, the time complexity of this algorithm is O(n log n), where n is the number of intervals.

A Java implementation of the second algorithm follows. The `IntervalComp` class is a [`Comparator`](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html) used for sorting.

{% highlight java %}
class Solution {
    /**
     * @param intervals: Sorted interval list.
     * @return: A new sorted interval list.
     */
    public List<Interval> merge(List<Interval> intervals) {
        if(intervals == null || intervals.isEmpty())
            return intervals;
        Collections.sort(intervals, new IntervalComp());
        int i = 1;
        while(i < intervals.size()) {
            Interval prev = intervals.get(i - 1);
            Interval curr = intervals.get(i);
            
            //3 ways intervals a, b overlap:
            //1. a covers b (complete overlap)
            //2. a covers b.start
            //3. a covers b.end
            
            //prev totally covers curr
            //curr.start >= prev.start is assumed because of sorting
            if(curr.start <= prev.end && curr.end <= prev.end) {
                intervals.remove(i);
            }
            //prev covers curr.start
            else if(curr.start >= prev.start && curr.start <= prev.end)
            {
                prev.end = curr.end;
                intervals.remove(i);
            }
            //prev covers corr.end: this case shouldn't happen.
            //else if(curr.end >= prev.start && curr.end <= prev.end) {
            //    prev.start = curr.start;
            //    intervals.remove(i);
            //}
            
            //No overlap
            else {
                i++;
            }
        }
        return intervals;
    }

}

class IntervalComp implements Comparator<Interval> {
    public int compare(Interval a, Interval b) {
        if(a.start < b.start)
            return -1;
        else if(a.start > b.start)
            return 1;
        else
            return 0;
    }
}

/**
 * Definition of Interval:
 * public class Interval {
 *     int start, end;
 *     Interval(int start, int end) {
 *         this.start = start;
 *         this.end = end;
 *     }
 */
 {% endhighlight %}
