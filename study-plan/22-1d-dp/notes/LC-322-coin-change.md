# LC 322 · Coin Change

| 項目 | 內容 |
|------|------|
| Pattern | DP |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Coin Change](https://leetcode.com/problems/coin-change/) |

**題意：** 用最少硬幣湊出金額 `amount`（無解回 -1）。

**核心：** 完全背包：`dp[a]=min(dp[a], dp[a-c]+1)`，初值 `amount+1` 表無窮。

```java
public int coinChange(int[] coins, int amount) {
    int[] dp = new int[amount + 1];
    Arrays.fill(dp, amount + 1);
    dp[0] = 0;
    for (int a = 1; a <= amount; a++) {
        for (int c : coins) {
            if (c <= a) dp[a] = Math.min(dp[a], dp[a - c] + 1);
        }
    }
    return dp[amount] > amount ? -1 : dp[amount];
}
```

**複雜度：** 時間 O(amount·|coins|) · 空間 O(amount)
