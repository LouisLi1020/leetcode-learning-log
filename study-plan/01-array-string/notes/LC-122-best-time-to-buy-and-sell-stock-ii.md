# LC 122 · Best Time to Buy and Sell Stock II

| 項目 | 內容 |
|------|------|
| Pattern | Greedy daily profit |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/) |

**題意：** 可多次交易、同時只持一股，求最大利潤。

**核心：** **貪心**：累加所有上漲日差 prices[i]-prices[i-1]。

```java
public int maxProfit(int[] prices) {
    int profit = 0;
    for (int i = 1; i < prices.length; i++) {
        if (prices[i] > prices[i - 1]) profit += prices[i] - prices[i - 1];
    }
    return profit;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
