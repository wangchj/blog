---
layout: post
title: Remove Linked List Elements
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
---

Given a singly linked list of integers and a target value, remove all instances of the target from the list.

Example

```
List          Target    Result
1->2->3       2         1->3
1->1->2->3    1         2->3
1->3->1->2    1         3->2
```

{% highlight java %}
public class Solution {
    /**
     * @param head a ListNode
     * @param val an integer
     * @return a ListNode
     */
    public ListNode removeElements(ListNode head, int val) {
        if(head == null)
            return null;
        
        ListNode node = head;
        ListNode prev = null;
        
        while(node != null) {
            if(node.val != val) {
                prev = node;
                node = node.next;
                continue;
            }
            
            if(node == head) {
                head = node = node.next;
            }
            else {
                prev.next = node.next;
                node = node.next;
            }
        }
        
        return head;
    }
}
{% endhighlight %}