---
title: "number-of-islands"
date: 2024-03-04
layout: post
---

```kotlin
class Solution {
    private lateinit var visited: Array<BooleanArray>
    private var count: Int = 0
    fun numIslands(grid: Array<CharArray>): Int {
        visited = Array(grid.size) { BooleanArray(grid[0].size) }
        count = 0

        for (i in grid.indices) {
            for (j in grid[0].indices) {
                if (dfs(grid, i, j)) {
                    count++
                }
            }
        }

        return count
    }

    private fun dfs(grid: Array<CharArray>, x: Int, y: Int): Boolean {
        if (x < 0 || x >= grid.size || y < 0 || y >= grid[0].size) return false
        if (grid[x][y] == '0' || visited[x][y]) return false

        visited[x][y] = true
        dfs(grid, x - 1, y)
        dfs(grid, x + 1, y)
        dfs(grid, x, y - 1)
        dfs(grid, x, y + 1)
        return true
    }
}
```
