# LC 72 · Edit Distance

| 項目 | 內容 |
|------|------|
| Pattern | DP 2D |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Edit Distance](https://leetcode.com/problems/edit-distance/) |

**題意：** 將 `word1` 變成 `word2` 的最少操作（增刪替）。

**核心：** `dp[i][j]`：若 `w1[i-1]==w2[j-1]` 則 `dp[i-1][j-1]`；否則 `1+min(上,左,左上)`。

```java
public int minDistance(String word1, String word2) {
    int m = word1.length(), n = word2.length();
    int[][] dp = new int[m + 1][n + 1];
    for (int i = 0; i <= m; i++) dp[i][0] = i;
    for (int j = 0; j <= n; j++) dp[0][j] = j;
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (word1.charAt(i - 1) == word2.charAt(j - 1))
                dp[i][j] = dp[i - 1][j - 1];
            else
                dp[i][j] = 1 + Math.min(dp[i - 1][j - 1],
                        Math.min(dp[i - 1][j], dp[i][j - 1]));
        }
    }
    return dp[m][n];
}
```

**複雜度：** 時間 O(mn) · 空間 O(mn)
