# LC 70 · Climbing Stairs

| 項目 | 內容 |
|------|------|
| Pattern | DP |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) |

**題意：** 每次爬 1 或 2 階，到頂有幾種方法。

**核心：** `dp[i]=dp[i-1]+dp[i-2]`；滾動兩變數。

```java
public int climbStairs(int n) {
    if (n <= 2) return n;
    int a = 1, b = 2;
    for (int i = 3; i <= n; i++) {
        int c = a + b;
        a = b;
        b = c;
    }
    return b;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
