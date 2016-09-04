---
layout: post
title: Word Search
categories: lintcode
tags:
- Java
- Algorithm
- Recursion
- Depth First Search
- Backtracking
- Amazon
- Facebook
---

Given a 2D board and a word, find if the word exists in the grid. The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

Example

```
H, U, T
O, L, K
M, E, E

word = "HULK" -> true
word = "HOME" -> true
word = "MEEK" -> true
word = "MELT" -> false
word = "HULOH" -> false
```

Using depth-first search

{% highlight java %}
public class Solution {
    public boolean exist(char[][] board, String word) {
        Set<Integer> visited = new HashSet<>();
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                if (dfs(board, word, i, j, 0, visited))
                    return true;
            }
        }
        return false;
    }
    
    /**
     * Return true if word is found; false otherwise.
     */
    boolean dfs(char[][] board, String word, int row, int col,
        int p, Set<Integer> visited)
    {
        if (row < 0 || row >= board.length ||
            col < 0 || col >= board[0].length)
            return false;
        
        //If cell already visited, return false
        if (visited.contains(row * board[0].length + col))
            return false;
        
        //If character does not match, return false
        if (board[row][col] != word.charAt(p))
            return false;
        
        //If found, return true
        if (p == word.length() - 1 && board[row][col] == word.charAt(p))
            return true;
        
        //Set current cell as visited    
        visited.add(row * board[0].length + col);
        
        //Recursive search
        if (dfs(board, word, row - 1, col, p + 1, visited))
            return true;
        if (dfs(board, word, row + 1, col, p + 1, visited))
            return true;
        if (dfs(board, word, row, col - 1, p + 1, visited))
            return true;
        if (dfs(board, word, row, col + 1, p + 1, visited))
            return true;
        
        //Set current cell as unvisited before return
        visited.remove(row * board[0].length + col);
        
        return false;
    }
}
{% endhighlight %}