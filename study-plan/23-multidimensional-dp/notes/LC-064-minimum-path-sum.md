# LC 64 · Minimum Path Sum

| 項目 | 內容 |
|------|------|
| Pattern | DP grid |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/) |

**題意：** 網格從左上到右下最小路徑和（只能右或下）。

**核心：** `dp[i][j]=grid[i][j]+min(上,左)`；第一行/列累加。

```java
public int minPathSum(int[][] grid) {
    int m = grid.length, n = grid[0].length;
    for (int i = 1; i < m; i++) grid[i][0] += grid[i - 1][0];
    for (int j = 1; j < n; j++) grid[0][j] += grid[0][j - 1];
    for (int i = 1; i < m; i++)
        for (int j = 1; j < n; j++)
            grid[i][j] += Math.min(grid[i - 1][j], grid[i][j - 1]);
    return grid[m - 1][n - 1];
}
```

**複雜度：** 時間 O(mn) · 空間 O(1)（原地）
