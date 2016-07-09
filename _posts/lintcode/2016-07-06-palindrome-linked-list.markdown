---
layout: post
title: Palindrome Linked List
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
---

Implement a function to check if a linked list is a palindrome. Can you do it in O(n) time and O(1) space?

Example

```
List             Result
1->2->1          true
1->2->3->2->1    true
1->2             false
```

{% highlight java %}
public class Solution {
    /**
     * @param head a ListNode
     * @return a boolean
     */
    public boolean isPalindrome(ListNode head) {
        if(head == null || head.next == null)
            return true;
            
        int len = getLength(head);
        ListNode tail = splitList(head, len);
        tail = reverseList(tail);
        for(int i = 0; i < len / 2; i++) {
            if(head.val != tail.val)
                return false;
            head = head.next;
            tail = tail.next;
        }
        return true;
    }
    
    /**
     * Return the second half of the list
     */
    private ListNode splitList(ListNode head, int length) {
        //Count of first half
        int count = length % 2 == 0 ? length / 2 : length / 2 + 1;
        for(int i = 1; i < count; i++)
            head = head.next;
        return head.next;
    }
    
    private ListNode reverseList(ListNode head) {
        ListNode next = head.next;
        head.next = null;
        while(next != null) {
            ListNode tail = next.next;
            next.next = head;
            head = next;
            next = tail;
        }
        return head;
    }
    
    private int getLength(ListNode head) {
        if(head == null)
            return 0;
        int res = 0;
        while(head != null) {
            res++;
            head = head.next;
        }
        return res;
    }
}
{% endhighlight %}