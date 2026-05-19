# LC 188 · Best Time to Buy and Sell Stock IV

| 項目 | 內容 |
|------|------|
| Pattern | DP |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/) |

**題意：** 最多 **k 次** 交易的最大利潤。

**核心：** `dp[t][0/1]` 第 t 次交易後不持倉/持倉最大利；`k` 大時等價無限次（LC122）。

```java
public int maxProfit(int k, int[] prices) {
    int n = prices.length;
    if (k >= n / 2) {
        int profit = 0;
        for (int i = 1; i < n; i++)
            if (prices[i] > prices[i - 1]) profit += prices[i] - prices[i - 1];
        return profit;
    }
    int[] buy = new int[k + 1], sell = new int[k + 1];
    Arrays.fill(buy, Integer.MIN_VALUE / 2);
    for (int p : prices) {
        for (int t = 1; t <= k; t++) {
            buy[t] = Math.max(buy[t], sell[t - 1] - p);
            sell[t] = Math.max(sell[t], buy[t] + p);
        }
    }
    return sell[k];
}
```

**複雜度：** 時間 O(nk) · 空間 O(k)
