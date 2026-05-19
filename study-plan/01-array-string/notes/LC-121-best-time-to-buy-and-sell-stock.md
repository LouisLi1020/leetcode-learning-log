# LC 121 · Best Time to Buy and Sell Stock

| 項目 | 內容 |
|------|------|
| Pattern | Greedy / min price |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) |

**題意：** 最多一次買賣，求最大利潤。

**核心：** 維護**最低買價** minPrice，每天更新 maxProfit = max(賣-買)。

```java
public int maxProfit(int[] prices) {
    int minPrice = prices[0], maxProfit = 0;
    for (int i = 1; i < prices.length; i++) {
        minPrice = Math.min(minPrice, prices[i]);
        maxProfit = Math.max(maxProfit, prices[i] - minPrice);
    }
    return maxProfit;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
