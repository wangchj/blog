---
layout: post
title: Intersection of Two Linked Lists
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
---

Write a program to find the node at which the intersection of two singly linked lists begins. If the two linked lists have no intersection at all, return null. The linked lists must retain their original structure after the function returns. You may assume there are no cycles anywhere in the entire linked structure.

Example

```
A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3

For lists A and B, the intersection begins at node c1.
```

The following implements insertion sort.

{% highlight java %}
public class Solution {
    /**
     * @param headA: the first list
     * @param headB: the second list
     * @return: a ListNode 
     */
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        int a = length(headA);
        int b = length(headB);
        int d = a > b ? a - b : b - a;
        
        for (int i = 0; i < d; i++) {
            if (a > b)
                headA = headA.next;
            else
                headB = headB.next;
        }
        
        while (headA != null && headB != null) {
            if (headA == headB)
                return headA;
            headA = headA.next;
            headB = headB.next;
        }
        
        return null;
    }
    
    public int length(ListNode head) {
        int res = 0;
        while (head != null) {
            res++;
            head = head.next;
        }
        return res;
    }
}
{% endhighlight %}