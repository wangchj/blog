---
layout: post
title: Merge k Sorted Lists
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
- Divide and Conquer
- Priority Queue
- Heap
- Uber
- Google
- Twitter
- LinkedIn
- Airbnb
- Facebook
---

Merge `k` sorted linked lists and return it as one sorted list.

Analyze and describe its complexity.

Example

```
Given k lists

2->4
1->3->5
1->2->3

Return

1->1->2->2->3->3->4->5

```

The following algorithm uses `k` pointers (indexes), one for each list. At each iteration, the minimum item is found out of `k` items and inserted into the new list.

{% highlight java %}
public class Solution {
    public ListNode mergeKLists(List<ListNode> lists) {  
        ListNode[] pointers = initPointers(lists);
        ListNode head = null, tail = null;
        
        ListNode min = getMin(pointers);
        while (min != null) {
            if (head == null)
                head = tail = min;
            else
                tail = tail.next = min;
            
            min = getMin(pointers);
        }
        
        return head;
    }
    
    ListNode[] initPointers(List<ListNode> lists) {
        ListNode[] pointers = new ListNode[lists.size()];
        for (int i = 0; i < lists.size(); i++)
            pointers[i] = lists.get(i);
        return pointers;
    }
    
    ListNode getMin(ListNode[] pointers) {
        ListNode min = null;
        int minIndex = 0;
        
        for (int i = 0; i < pointers.length; i++) {
            if (pointers[i] == null)
                continue;
            if (min == null || pointers[i].val < min.val) {
                min = pointers[i];
                minIndex = i;
            }
        }
        
        if (min != null)
            pointers[minIndex] = pointers[minIndex].next;
        
        return min;
    }
}
{% endhighlight %}

{% highlight java %}
public class ListNode {
  int val;
  ListNode next;
  ListNode(int val) {
    this.val = val;
    this.next = null;
  }
}
{% endhighlight %}