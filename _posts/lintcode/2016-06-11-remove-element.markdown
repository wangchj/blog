---
layout: post
title: Remove Element
categories: lintcode
tags:
- Java
- algorithm
- Array
- Two Pointers
---

Given an array and a value, remove all occurrences of that value in place and return the new length.

The order of elements can be changed, and the elements after the new length don't matter.

Example

Given an array `[0,4,4,0,0,2,4,4]`, value=4

return `4` and front four elements of the array is `[0,0,0,2]`

{% highlight java %}
public class Solution {
    /** 
     *@param A: A list of integers
     *@param elem: An integer
     *@return: The new length after remove
     */
    public int removeElement(int[] A, int elem) {
        //Find the first elem from the back
        int back = A.length - 1;
        while(back >= 0 && A[back] == elem)
            back--;
        int len = back + 1;
        
        if(back < 0)
            return 0;
        if(back == 0)
            return 1;
        
        int front = 0;
        
        while(front < back) {
            if(A[front] == elem) {
                
                //Swap A[front] and A[back]
                A[front] ^= A[back];
                A[back] ^= A[front];
                A[front] ^= A[back];
                
                //Decrement back
                while(A[back] == elem) {
                    back--;
                    len--;
                }
            }
            front++;
        }
        
        return len;
    }
}
{% endhighlight %}