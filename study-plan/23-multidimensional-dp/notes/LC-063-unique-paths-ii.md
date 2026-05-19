# LC 63 · Unique Paths II

| 項目 | 內容 |
|------|------|
| Pattern | DP grid |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Unique Paths II](https://leetcode.com/problems/unique-paths-ii/) |

**題意：** 有障礙物時，左上到右下路徑數。

**核心：** `dp[i][j]`：若 `obstacle` 則 0，否則 `左+上`；第一行/列遇障礙後全 0。

```java
public int uniquePathsWithObstacles(int[][] obstacleGrid) {
    int m = obstacleGrid.length, n = obstacleGrid[0].length;
    if (obstacleGrid[0][0] == 1) return 0;
    int[] dp = new int[n];
    dp[0] = 1;
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            if (obstacleGrid[i][j] == 1) dp[j] = 0;
            else if (j > 0) dp[j] += dp[j - 1];
        }
    }
    return dp[n - 1];
}
```

**複雜度：** 時間 O(mn) · 空間 O(n)
