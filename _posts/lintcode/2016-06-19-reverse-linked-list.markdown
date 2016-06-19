---
layout: post
title: Reverse Linked List
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
- Facebook
- Uber
- Amazon
---

Reverse a linked list in-place and in one-pass.

Example

```
1->2->3  =>  3->2->1
```

The algorithm should run in-place with O(1) space and O(n) time.

{% highlight java %}
public class Solution {
    /**
     * @param head: The head of linked list.
     * @return: The new head of reversed linked list.
     */
    public ListNode reverse(ListNode head) {
        if(head == null || head.next == null)
            return head;
        ListNode res = reverse(head.next);
        ListNode last = head.next;
        head.next = null;
        last.next = head;
        return res;
    }
}
{% endhighlight %}