# LC 97 · Interleaving String

| 項目 | 內容 |
|------|------|
| Pattern | DP 2D |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Interleaving String](https://leetcode.com/problems/interleaving-string/) |

**題意：** 判斷 `s3` 是否為 `s1`、`s2` 交錯組成。

**核心：** `dp[i][j]`：前 `i+j` 字元能否由 `s1[0..i)` 與 `s2[0..j)` 交錯；轉移看 `s1[i-1]` 或 `s2[j-1]` 是否匹配 `s3[i+j-1]`。

```java
public boolean isInterleave(String s1, String s2, String s3) {
    int m = s1.length(), n = s2.length();
    if (m + n != s3.length()) return false;
    boolean[][] dp = new boolean[m + 1][n + 1];
    dp[0][0] = true;
    for (int i = 1; i <= m; i++) dp[i][0] = dp[i - 1][0] && s1.charAt(i - 1) == s3.charAt(i - 1);
    for (int j = 1; j <= n; j++) dp[0][j] = dp[0][j - 1] && s2.charAt(j - 1) == s3.charAt(j - 1);
    for (int i = 1; i <= m; i++)
        for (int j = 1; j <= n; j++)
            dp[i][j] = (dp[i - 1][j] && s1.charAt(i - 1) == s3.charAt(i + j - 1))
                    || (dp[i][j - 1] && s2.charAt(j - 1) == s3.charAt(i + j - 1));
    return dp[m][n];
}
```

**複雜度：** 時間 O(mn) · 空間 O(mn)
