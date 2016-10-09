---
layout: post
title: Linked List Cycle II
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
- Two Pointers
---

Given a linked list, return the node where the cycle begins.

If there is no cycle, return null.

The following uses a hash set to track the nodes that has already been visited. The space complexity is O(n), where n is the number of nodes in the list.

{% highlight java %}
public class Solution {
    public ListNode detectCycle(ListNode head) {  
        if (head == null) return null;
        
        HashSet<ListNode> visited = new HashSet<>();
      
        for (ListNode node = head; node != null; node = node.next) {
            if (visited.contains(node))
                return node;
                
            visited.add(node);
        }
        
        return null;
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