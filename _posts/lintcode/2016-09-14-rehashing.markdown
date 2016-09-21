---
layout: post
title: Rehashing
categories: lintcode
tags:
- Java
- Algorithm
- Hash Table
---

The size of the hash table is not determinate at the very beginning. If the total size of keys is too large (e.g. size >= capacity / 10), we should double the size of the hash table and rehash every keys. Say you have a hash table looks like below:

```
size=3, capacity=4

[null, 21, 14, null]
       ↓    ↓
       9   null
       ↓
      null
```

The hash function is:

```
int hashcode(int key, int capacity) {
    return key % capacity;
}
```

Here we have three numbers, `9`, `14` and `21`, where `21` and `9` share the same position as they all have the same hashcode `1` (21 % 4 = 9 % 4 = 1). We store them in the hash table by linked list.

Rehashing this hash table, double the capacity, you will get:

```
size=3, capacity=8

index:   0    1    2    3     4    5    6   7
hash : [null, 9, null, null, null, 21, 14, null]
```

For this problem, given the original hash table, return the new hash table after rehashing.

Notice

For negative integer in hash table, the position can be calculated as follow:

C++/Java: if you directly calculate `-4 % 3` you will get `-1`. You can use function: `a % b = (a % b + b) % b` to make it is a non negative integer.
Python: you can directly use `-1 % 3`, you will get `2` automatically.

Example

```
Original Table:

[null, 21, 14, null]
       ↓    ↓
       9   null
       ↓
      null


Rehashed Table: 

[null, 9, null, null, null, 21, 14, null]
       ↓                    ↓    ↓
      null                 null null

```

{% highlight java %}
public class Solution {   
    public ListNode[] rehashing(ListNode[] hashTable) {
        ListNode[] table = new ListNode[hashTable.length * 2];
        
        for (ListNode head : hashTable) {
            if (head == null)
                continue;
            for (ListNode p = head; p != null; p = p.next)
                insert(table, p);
        }
        
        return table;
    }
    
    void insert(ListNode[] table, ListNode node) {
        int code = hash(node.val, table.length);
        if (table[code] == null)
            table[code] = new ListNode(node.val);
        else {
            ListNode p = table[code];
            while (p.next != null)
                p = p.next;
            p.next = new ListNode(node.val);
        }
    }
    
    int hash(int key, int cap) {
        return (key % cap + cap) % cap;
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