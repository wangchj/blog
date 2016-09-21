---
layout: post
title: Rotate List
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
---

Given a list, rotate the list to the right by `k` places, where `k` is non-negative.

Example

```
List             k    Result
1->2->3->4->5    0    1->2->3->4->5
1->2->3->4->5    2    4->5->1->2->3
1->2->3->4->5    5    1->2->3->4->5
```

{% highlight java %}
public class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        int len = getLength(head);
        
        if (k == 0 || len == 0 || k % len == 0)
            return head;
        
        ListNode last = getLastNode(head);
        ListNode prev = null;
        ListNode node = head;
        int count = len - (k % len);
        
        //Find cut point
        while (count != 0) {
            prev = node;
            node = node.next;
            count--;
        }
        
        prev.next = null;
        last.next = head;
        return node;
    }
    
    int getLength(ListNode head) {
        int res = 0;
        while (head != null) {
            res++;
            head = head.next;
        }
        return res;
    }
    
    ListNode getLastNode(ListNode head) {
        while (head.next != null)
            head = head.next;
        return head;
    }
}
{% endhighlight %}

{% highlight java %}
public class ListNode {
    int val;
    ListNode next;
    ListNode(int x) {
        val = x;
        next = null;
    }
}
{% endhighlight %}