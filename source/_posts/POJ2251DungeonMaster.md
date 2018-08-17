---
title: POJ2251DungeonMaster
date: 2018-08-15 15:22:17
tags:
  - acm
  - bfs
categories:
  - kuangbin带你飞 专题一 简单搜索
---
[kuangbin带你飞专题](https://vjudge.net/article/187)
# 题目
[POJ1321](https://vjudge.net/problem/POJ-2251)
You are trapped in a 3D dungeon and need to find the quickest way out! The dungeon is composed of unit cubes which may or may not be filled with rock. It takes one minute to move one unit north, south, east, west, up or down. You cannot move diagonally and the maze is surrounded by solid rock on all sides.

Is an escape possible? If yes, how long will it take?
## Input
The input consists of a number of dungeons. Each dungeon description starts with a line containing three integers L, R and C (all limited to 30 in size).
L is the number of levels making up the dungeon.
R and C are the number of rows and columns making up the plan of each level.
Then there will follow L blocks of R lines each containing C characters. Each character describes one cell of the dungeon. A cell full of rock is indicated by a '#' and empty cells are represented by a '.'. Your starting position is indicated by 'S' and the exit by the letter 'E'. There's a single blank line after each level. Input is terminated by three zeroes for L, R and C.
## Output
Each maze generates one line of output. If it is possible to reach the exit, print a line of the form
Escaped in x minute(s).

where x is replaced by the shortest time it takes to escape.
If it is not possible to escape, print the line
Trapped!
## Sample Input
``` c++
3 4 5
S....
.###.
.##..
###.#

#####
#####
##.##
##...

#####
#####
#.###
####E

1 3 3
S##
#E#
###

0 0 0
```
## Sample Output
``` c++
Escaped in 11 minute(s).
Trapped!
```
# 思路
题意大致是一个三层迷宫，从出发点S到终点E，求最少时间，考虑广搜求解最优解问题，使用队列保存每步的坐标，每次移动有6种情况可以用一个二维数组来表示，设一个visit数组来表示到每个位置的最少时间，每次都是以能够到达该位置的前一个位置的最少时间+1来更新。
# 代码
``` c++
#include <iostream>
#include <cstdio>
//#include <memory.h>

using namespace std;

int n, k;
char pan[10][10];
int row[10];
int col[10];
int sum;
int res;

void dfs(int sum, int a){
    if(sum == k){
        res++;
        return;
    }
    for(int i = a; i < n; i++){
        for(int j = 0; j < n; j++){
            if(pan[i][j] == '#' && !row[i] && !col[j]){
                row[i] = 1;
                col[j] = 1;
                dfs(sum+1, i+1);
                row[i] = 0;
                col[j] = 0;
            }
        }
    }
}

int main()
{
    while(scanf("%d %d", &n, &k) && n != -1){
        //memset(row, 0, sizeof(row));
        //memset(col, 0, sizeof(col));
        for(int i = 0; i < n; i++){
            row[i] = col[i] = 0;
        }
        res = 0;
        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                scanf(" %c", &pan[i][j]);
            }
        }

        dfs(0, 0);

        printf("%d\n", res);
    }

    return 0;
}

```
