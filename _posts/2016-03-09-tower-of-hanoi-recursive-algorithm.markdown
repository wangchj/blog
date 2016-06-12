---
layout: post
status: publish
published: true
title: Tower of Hanoi Recursive Algorithm
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1534
wordpress_url: http://codenuggets.com/?p=1534
date: '2016-03-09 18:09:35 -0600'
date_gmt: '2016-03-09 18:09:35 -0600'
categories:
- Uncategorized
tags:
- Java
- recursion
- algorithm
- Tower of Hanoi
comments: []
---
<img src="http://media.tumblr.com/39965510828526d93b428ca064e71410/tumblr_inline_mutp1vmLcY1rtan47.jpg">

The Tower of Hanoi is a puzzle, for which the goal is to move all disks from peg A to C, with the following rules for each move:

1. Any pegs can be used to temporarily store a disk
2. Disks can only be taken from the top of a stack
3. Only a smaller disk can be place on top of a larger disk

An interactive version of the game can be found at [mathisfun.com](https://www.mathsisfun.com/games/towerofhanoi.html).

## Algorithm
A simple algorithm to find the optimal moves for the game is to use recursion. The idea is continuous reduction of the problem size by one.

For example, let's say we have N disks, moving from A to C. This can be reduced to moving N-1 disks to B, then after that we just have to move one bottom disk from A to C. Last step is to move N-1 disk from B to C, which is also solved recursively.

## Implementation
The `solve()` method below implements the recursive algorithm. The following are the parameters:

1. `n`: the number of disks to move
2. `from`: the source peg number
3. `to`: the destination peg number
4. `temp`: the temporary peg

For example, the following `main()` method solves the puzzle of 4 disks, moving from peg 1 to peg 3, using peg 2 as temporary storage.

{% highlight java %}
public class Hanoi {
    public static void solve(int n, int from, int to, int temp) {
        if(n <= 0)
            return;
        if(n == 1) {
            moveOneDisk(from, to);
            return;
        }
        solve(n - 1, from, temp, to);
        moveOneDisk(from, to);
        solve(n - 1, temp, to, from);
    }
    
    public static void moveOneDisk(int from, int to) {
        System.out.printf("Move disk from %d to %d %n", from, to);
    }
    
    public static void main(String[] args) {
        solve(4, 1, 3, 2);
    }
}
{% endhighlight %}