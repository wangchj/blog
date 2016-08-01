---
layout: post
title: Implement Queue by Two Stacks
categories: lintcode
tags:
- Java
- Algorithm
- Stack
- Queue
- LintCode Copyright
---

Implement a queue using only two stacks.

The queue has the following operations:

1. `push()`: put an item at the end of the queue.
2. `pop()`: remove an item from the front of the queue.
3. `top()`: get an item from the front of the queue, but does not remove the item.

Implement by using two stacks, do not use any other data structure and `push()`, `pop()` and `top()` should be O(1) by AVERAGE.

Example

```
push(1)
pop()     // return 1
push(2)
push(3)
top()     // return 2
pop()     // return 2
```

Recursive solution:

{% highlight java %}
public class Queue {
    private Stack<Integer> stack1;
    private Stack<Integer> stack2;

    public Queue() {
        stack1 = new Stack<>();
        stack2 = new Stack<>();
    }
    
    public void push(int element) {
        int size = stack2.size();
        for (int i = 0; i < size; i++)
            stack1.push(stack2.pop());
        stack1.push(element);
    }

    public int pop() {
        int size = stack1.size();
        for (int i = 0; i < size; i++)
            stack2.push(stack1.pop());
        return stack2.pop();
    }

    public int top() {
        int size = stack1.size();
        for (int i = 0; i < size; i++)
            stack2.push(stack1.pop());
        return stack2.peek();
    }
}
{% endhighlight %}