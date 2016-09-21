---
layout: post
title: Reorder List
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
- Two Pointers
---

Given a singly linked list, L = {n<sub>1</sub>, n<sub>2</sub>, ..., n<sub>n-1</sub>, n<sub>n</sub>}, reorder it so that L = {n<sub>1</sub>, n<sub>n</sub>, n<sub>2</sub>, n<sub>n-1</sub>, ...}. Rearrange the nodes not just the values. Do it in place.

Example

```
Input         Result
1->2->3->4    1->4->2->3
1->2          1->2
```

The following algorithm maps the list to an array and reorders the nodes in the array. This is a simple solution. The time and space complexity is both O(n) where `n` is the number of nodes in the list. However, I got 'Memory Limit Exceeded' for this algorithm.

{% highlight java %}
public class Solution {
    public void reorderList(ListNode head) {  
        int len = getLength(head);
        if (len < 3) return;
        ListNode[] nodes = getArray(head, len);
        int i = 0, j = len - 1;
        while (j > i + 1) {
            nodes[i].next = nodes[j];
            nodes[j].next = nodes[i + 1];
            i++;
            j--;
        }
    }
    
    int getLength(ListNode head) {
        int len = 0;
        while (head != null) {
            len++;
            head = head.next;
        }
        return len;
    }
    
    // Get an array of the nodes
    ListNode[] getArray(ListNode head, int len) {
        ListNode[] nodes = new ListNode[len];
        for (int i = 0; i < len; i++, head = head.next)
            nodes[i] = head;
        return nodes;
    }
}
{% endhighlight %}

I got accepted for the following algorithm. The time complexity is O(n<sup>2</sup>), and space complexity O(1).

{% highlight java %}
public class Solution {
    /**
     * @param head: The head of linked list.
     * @return: void
     */
    public void reorderList(ListNode head) {  
        if (head == null)
            return;
        
        //The very last two nodes of the list    
        ListNode[] tail = getLastTwoNodes(head);
        
        while (tail[0] != head && tail[1] != head) {
            tail[0].next = null;
            tail[1].next = head.next;
            head.next = tail[1];
            
            head = head.next.next;
            tail = getLastTwoNodes(head);
        }
    }
    
    //Get the last and second to last nodes of the list.
    //Index 0 is second to last, index 1 is the last node.
    ListNode[] getLastTwoNodes(ListNode head) {
        ListNode[] n = new ListNode[2];
        n[1] = head;
        
        while (n[1].next != null) {
            n[0] = n[1];
            n[1] = n[1].next;
        }
        
        return n;
    }
}
{% endhighlight %}

{% highlight java %}
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}
{% endhighlight %}
