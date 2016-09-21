---
layout: post
title: Flatten Nested List Iterator
categories: lintcode
tags:
- Java
- Algorithm
- Recursion
- Stack
- Data Structure Design
- Google
---

Given a nested list of integers, implement an iterator to flatten it.

Each element is either an integer, or a list -- whose elements may also be integers or other lists.

Example

```
Input              Result
[1, 2, 3]          [1, 2, 3]
[[1,1],2,[1,1]]    [1,1,2,1,1]
[1,[4,[6]]]        [1,4,6]
```
We use the following `ListIndex` class for backtracking.

{% highlight java %}
class ListIndex {
    public List<NestedInteger> list;
    public int index;
    
    public ListIndex(List<NestedInteger> list, int index) {
        this.list = list;
        this.index = index;
    }
}
{% endhighlight %}

The following algorithm uses the `ListIndex` class above to perform the search using a stack.

{% highlight java %}
import java.util.Iterator;

public class NestedIterator implements Iterator<Integer> {
    Stack<ListIndex> stack;   //Stack for backtracking
    List<NestedInteger> curr; //The current list
    int index;                //The current index
    
    public NestedIterator(List<NestedInteger> nestedList) {
        stack = new Stack<ListIndex>();
        curr = nestedList;
        index = -1;
        findNext();
    }

    /**
     * Find the next non-list integer.
     */
    private void findNext() {
        while (true) {
            index++;
            //If we reach the end of this list, then, we either
            //pop the stack to backtrack or we are finished.
            if (index == curr.size()) {
                //Reached the end of everything
                if (stack.isEmpty())
                    return;
                
                //Pop the stack to backtrack
                ListIndex listIndex = stack.pop();
                curr = listIndex.list;
                index = listIndex.index;
            }
            else { //Index is not at the end of current list
                NestedInteger i = curr.get(index);
                
                //Found next item
                if (i.isInteger())
                    return;
                
                //Push current list and search child list
                stack.push(new ListIndex(curr, index));
                curr = i.getList();
                index = -1;
            }
        }
    }
    
    // @return {int} the next element in the iteration
    @Override
    public Integer next() {
        Integer res = curr.get(index).getInteger();
        findNext();
        return res;
    }

    // @return {boolean} true if the iteration has more element or false
    @Override
    public boolean hasNext() {
        return index < curr.size();
    }

    @Override
    public void remove() {}
    
    //Your NestedIterator object will be instantiated and called as such:
    NestedIterator i = new NestedIterator(nestedList);
    while (i.hasNext()) v.add(i.next());
}
{% endhighlight %}

{% highlight java %}
public interface NestedInteger {

    // @return true if this NestedInteger holds a single integer,
    // rather than a nested list.
    public boolean isInteger();

    // @return the single integer that this NestedInteger holds,
    // if it holds a single integer
    // Return null if this NestedInteger holds a nested list
    public Integer getInteger();

    // @return the nested list that this NestedInteger holds,
    // if it holds a nested list
    // Return null if this NestedInteger holds a single integer
    public List<NestedInteger> getList();
}
{% endhighlight %}