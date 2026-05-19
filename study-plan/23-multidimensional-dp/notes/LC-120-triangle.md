# LC 120 · Triangle

| 項目 | 內容 |
|------|------|
| Pattern | DP |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Triangle](https://leetcode.com/problems/triangle/) |

**題意：** 三角形從頂到底路徑最小和。

**核心：** 自底向上：`dp[j]=min(dp[j],dp[j+1])+triangle[i][j]`；可原地改最後一行。

```java
public int minimumTotal(List<List<Integer>> triangle) {
    int[] dp = new int[triangle.size()];
    List<Integer> last = triangle.get(triangle.size() - 1);
    for (int j = 0; j < dp.length; j++) dp[j] = last.get(j);
    for (int i = triangle.size() - 2; i >= 0; i--) {
        for (int j = 0; j <= i; j++) {
            dp[j] = Math.min(dp[j], dp[j + 1]) + triangle.get(i).get(j);
        }
    }
    return dp[0];
}
```

**複雜度：** 時間 O(n²) · 空間 O(n)
