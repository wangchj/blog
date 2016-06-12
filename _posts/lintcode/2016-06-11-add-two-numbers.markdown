---
layout: post
title: Add Two Numbers
categories: lintcode
tags:
- Java
- algorithm
- Cracking The Coding Interview
- Linked List
- High Precision
---

You have two numbers represented by a linked list, where each node contains a single digit. The digits are stored in reverse order, such that the 1's digit is at the head of the list. Write a function that adds the two numbers and returns the sum as a linked list.

Example

```
   7->1->6        3->1->5
+  5->9->2      + 5->9->2
-----------     ----------
   2->1->9        8->0->8
```

{% highlight java %}
public class Solution {
    /**
     * @param l1: the first list
     * @param l2: the second list
     * @return: the sum list of l1 and l2 
     */
    public ListNode addLists(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode res = null;
        ListNode tail = null;
        while(l1 != null || l2 != null) {
            int d1 = l1 == null ? 0 : l1.val;
            int d2 = l2 == null ? 0 : l2.val;
            int s = d1 + d2 + carry;
            carry = s / 10;
            ListNode node = new ListNode(s % 10);
            if(res == null)
                res = tail = node;
            else {
                tail.next = node;
                tail = tail.next;
            }
            if(l1 != null)
                l1 = l1.next;
            if(l2 != null)
                l2 = l2.next;
        }
        if(carry != 0) {
            if(res == null)
                res = new ListNode(1);
            else
                tail.next = new ListNode(1);
        }
        
        if(res == null)
            res = new ListNode(0);
            
        return res;
    }
}
{% endhighlight %}