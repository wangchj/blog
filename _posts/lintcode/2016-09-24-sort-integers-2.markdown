---
layout: post
title: Sort Integers II
categories: lintcode
tags:
- Java
- Algorithm
- Sort
- Merge Sort
- Quick Sort
---

Given an integer array, sort it in ascending order. Use quick sort, merge sort, heap sort or any O(nlogn) algorithm.

Example

```
Input              Result
[3, 2, 1]          [1, 2, 3]
[3, 2, 1, 4, 5]    [1, 2, 3, 4, 5]
```

The following is an implementation of merge sort, which has time complexity of O(nlogn) and space complexity of O(n).

{% highlight java %}
public class Solution {
    int[] temp;
    
    public void sortIntegers2(int[] a) {
        if (a == null || a.length == 0)
            return;
        temp = new int[a.length];
        mergeSort(a, 0, a.length - 1);
    }
    
    void mergeSort(int[] a, int left, int right) {
        if (a == null || a.length == 0 || left == right)
            return;
        
        int mid = (right - left) / 2 + left;
        mergeSort(a, left, mid);
        mergeSort(a, mid + 1, right);
        
        merge(a, left, mid, right);
    }
    
    void merge(int[] a, int left, int mid, int right) {
        for (int i = left; i <= right; i++)
            temp[i] = a[i];
            
        int j = left, k = mid + 1;
        
        for (int i = left; i <= right; i++) {
            if (j > mid)
                temp[i] = a[k++];
            else if (k > right)
                temp[i] = a[j++];
            else if (a[j] < a[k])
                temp[i] = a[j++];
            else
                temp[i] = a[k++];
        }
        
        for (int i = left; i <= right; i++)
            a[i] = temp[i];
    }
}
{% endhighlight %}
