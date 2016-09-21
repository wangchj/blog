---
layout: post
title: Linked List Cycle
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
- Two Pointers
- Hash Table
---

Given a linked list, determine if it has a cycle in it.


The following algorithm uses a hash map to keep track of nodes visited. The time and space complexity is both O(n) where n is the number of nodes in the list.

{% highlight java %}
public class Solution {
    public boolean hasCycle(ListNode head) {  
        if(head == null)
            return false;
        
        HashSet<ListNode> visited = new HashSet<>();
      
        for(ListNode current = head; current != null;
            current = current.next)
        {
            if(visited.contains(current))
                return true;
            visited.add(current);
        }
        
        return false;
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