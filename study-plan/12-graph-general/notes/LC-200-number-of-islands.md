# LC 200 · Number of Islands

| 項目 | 內容 |
|------|------|
| Pattern | DFS/BFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Number of Islands](https://leetcode.com/problems/number-of-islands/) |

**題意：** 二維 grid 中 `'1'` 陸地連通塊數量（四方向）。

**核心：** 掃描 grid：遇 `'1'` 計數並 DFS/BFS 沉沒整塊（改 `'0'` 防重訪）。

```java
public int numIslands(char[][] grid) {
    int m = grid.length, n = grid[0].length, count = 0;
    for (int i = 0; i < m; i++)
        for (int j = 0; j < n; j++)
            if (grid[i][j] == '1') {
                count++;
                dfs(grid, i, j);
            }
    return count;
}
void dfs(char[][] g, int r, int c) {
    if (r < 0 || c < 0 || r >= g.length || c >= g[0].length || g[r][c] != '1') return;
    g[r][c] = '0';
    dfs(g, r + 1, c); dfs(g, r - 1, c); dfs(g, r, c + 1); dfs(g, r, c - 1);
}
```

**複雜度：** O(mn) 時間，O(mn) 空間（最壞 DFS 棧）。
