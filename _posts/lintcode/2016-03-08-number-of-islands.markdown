---
layout: post
status: publish
published: true
title: Number of Islands
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1530
wordpress_url: http://codenuggets.com/?p=1530
date: '2016-03-08 21:42:11 -0600'
date_gmt: '2016-03-08 21:42:11 -0600'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- Facebook
- Google
- LintCode easy
- breadth-first search
- bfs
- Zenefit
comments: []
---
Given a boolean 2D matrix, find the number of islands.

Notice 0 is represented as the sea, 1 is represented as the island. If two 1 is adjacent, we consider them in the same island. We only consider up/down/left/right adjacent.

Example

Return `3` for the following graph.

```
[
  [1, 1, 0, 0, 0],
  [0, 1, 0, 0, 1],
  [0, 0, 0, 1, 1],
  [0, 0, 0, 0, 0],
  [0, 0, 0, 0, 1]
]
```

## Solution

We can use an easy breadth-first search algorithm, which follows:

We search each cell of the matrix. If the cell is a land (a 1), we increment our count, and perform bread-first search (BFS) expansion of that land, which is represented by `bfs()` method.

During the BFS expansion, for every connected land cell, we mark that as visited, which is recorded by the `v[][]` array. The sole purpose of the `bfs()` is to mark the connected land cells. The reason we want to do this, is that in the later search, when a land is found, but it is part of an island we already visited, then we do not increment the count.

{% highlight java %}
public class Solution {
    /**
     * @param grid a boolean 2D matrix
     * @return an integer
     */
    public int numIslands(boolean[][] grid) {
        if(grid == null || grid.length == 0)
            return 0;
        boolean[][] v = new boolean[grid.length][grid[0].length];
        int count = 0;
        for(int i = 0; i < grid.length; i++) {
            boolean[] row = grid[i];
            for(int j = 0; j < row.length; j++) {
                if(grid[i][j] && !v[i][j]) {
                    count++;
                    bfs(i, j, grid, v);
                }
            }
        }
        return count;
    }
    
    private void bfs(int i, int j, boolean[][] grid, boolean[][] v) {
        Queue<Point> q = new LinkedList<Point>();
        q.add(new Point(i, j));
        while(!q.isEmpty()) {
            Point p = q.remove();
            
            v[p.i][p.j] = true;
            
            //Enqueue neighbors in clockwise fashion: up, right, down, left
            
            if(p.i != 0 && grid[p.i - 1][p.j] && !v[p.i - 1][p.j])
                q.add(new Point(p.i - 1, p.j));
            if(p.j < v[0].length - 1 && grid[p.i][p.j + 1] && !v[p.i][p.j + 1])
                q.add(new Point(p.i, p.j + 1));
            if(p.i < v.length - 1 && grid[p.i + 1][p.j] && !v[p.i + 1][p.j])
                q.add(new Point(p.i + 1, p.j));
            if(p.j > 0 && grid[p.i][p.j - 1] && !v[p.i][p.j - 1])
                q.add(new Point(p.i, p.j - 1));
        }
    }
    
    class Point {
        int i, j;
        public Point(int i, int j) {
            this.i = i;
            this.j = j;
        }
    }
}
{% endhighlight %}