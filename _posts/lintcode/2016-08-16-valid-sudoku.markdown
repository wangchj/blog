---
layout: post
title: Valid Sudoku
categories: lintcode
tags:
- Java
- Algorithm
- Matrix
- Hash Table
- Uber
---

Given a Sudoku board, write an algorithm to determine if the board is valid.

Empty cell denoted by the period (`.`) character.

The rule of a valid Sudoku board can be found on [Wikipedia](https://en.wikipedia.org/wiki/Sudoku).

Example

The following board is valid

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/500px-Sudoku-by-L2G-20050714.svg.png" width="200">

{% highlight java %}
class Solution {
    public boolean isValidSudoku(char[][] board) {
        ArrayList<HashSet<Character>> r = new ArrayList<>();
        ArrayList<HashSet<Character>> c = new ArrayList<>();
        ArrayList<HashSet<Character>> s = new ArrayList<>();

        for(int i = 0; i < 9; i++) {
            r.add(new HashSet<Character>());
            c.add(new HashSet<Character>());
            s.add(new HashSet<Character>());
        }

        for(int row = 0; row < 9; row++) {
            for(int col = 0; col < 9; col++) {
                char val = board[row][col];
                
                if(val == '.')
                    continue;

                if(r.get(row).contains(val))
                    return false;
                else
                    r.get(row).add(val);

                if(c.get(col).contains(val))
                    return false;
                else
                    c.get(col).add(val);

                int square = getSquare(row, col);
                if(s.get(square).contains(val))
                    return false;
                else
                    s.get(square).add(val);
            }
        }
        return true;
    }

    public int getSquare(int row, int col) {
        row /= 3;
        col /= 3;
        return row * 3 + col;
    }
}
{% endhighlight %}