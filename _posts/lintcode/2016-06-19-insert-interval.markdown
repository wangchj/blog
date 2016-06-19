---
layout: post
title: Insert Interval
categories: lintcode
tags:
- Java
- Algorithm
- LinkedIn
- Google
---

Given a non-overlapping interval list which is sorted by start point. Insert a new interval into it, make sure the list is still in order and non-overlapping (merge intervals if necessary).

Example

Insert `[2, 5]` into `[[1,2], [5,9]]`, we get `[[1,9]]`.

Insert `[3, 4]` into `[[1,2], [5,9]]`, we get `[[1,2], [3,4], [5,9]]`.

{% highlight java %}
class Solution {
    /**
     * Insert newInterval into intervals.
     * @param intervals: Sorted interval list.
     * @param newInterval: A new interval.
     * @return: A new sorted interval list.
     */
    public ArrayList<Interval> insert(ArrayList<Interval> intervals, Interval newInterval) {
        //If the list of intervals is empty, we just have to add the new
        //interval and return
        if(intervals.isEmpty()) {
            intervals.add(newInterval);
            return intervals;
        }
        
        //Insert position
        int insert = -1;
        
        //Left and right used for binary search
        int left = 0;
        int right = intervals.size() - 1;
        
        //Use binary search to find insert position
        while(left <= right) {
            int mid = (right - left) / 2 + left;
            Interval midInterval = intervals.get(mid);
            if(newInterval.start == midInterval.start) {
                insert = mid;
                break;
            }
            
            //Break before left becomes larger than right, or vice versa, so left
            //pointer can be use at the next step
            if(left == right)
                break;
            
            if(newInterval.start < midInterval.start) {
                right = mid - 1;
            }
            else {
                left = mid + 1;
            }
        }
        
        //If overlapping interval found
        if(insert != -1) {
            intervals.get(insert).end = Math.max(intervals.get(insert).end, newInterval.end);
        }
        else {
            if(intervals.get(left).start < newInterval.start) {
                intervals.add(left + 1, newInterval);
                insert = left + 1;
            }
            else {
                intervals.add(left, newInterval);
                insert = left;
            }
        }
        
        //Check to see if new interval overlap with previous interval
        if(insert > 0 && intervals.get(insert).start <= intervals.get(insert - 1).end) {
            intervals.get(insert - 1).end = Math.max(intervals.get(insert - 1).end, intervals.get(insert).end);
            insert--;
        }    
        
        //Check to merge following intervals.
        while(true) {
            if(insert == intervals.size() - 1)
                break;
            
            //If overlap
            if(intervals.get(insert).end >= intervals.get(insert + 1).start) {
                intervals.get(insert).end = Math.max(intervals.get(insert).end, intervals.get(insert + 1).end);
                intervals.remove(insert + 1);
            }
            else
                break;
            
        }
        
        return intervals;
    }
}
{% endhighlight %}

{% highlight java %}
public classs Interval {
    int start, end;
    
    Interval(int start, int end) {
        this.start = start;
        this.end = end;
    }
}
{% endhighlight %}