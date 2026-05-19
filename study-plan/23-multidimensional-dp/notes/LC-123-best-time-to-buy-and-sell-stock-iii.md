# LC 123 · Best Time to Buy and Sell Stock III

| 項目 | 內容 |
|------|------|
| Pattern | DP |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/) |

**題意：** 最多兩筆交易，求最大利潤。

**核心：** 四狀態：**buy1/sell1/buy2/sell2**，依序轉移（第二筆用第一筆利潤）。

```java
public int maxProfit(int[] prices) {
    int buy1 = Integer.MAX_VALUE, sell1 = 0;
    int buy2 = Integer.MAX_VALUE, sell2 = 0;
    for (int p : prices) {
        buy1 = Math.min(buy1, p);
        sell1 = Math.max(sell1, p - buy1);
        buy2 = Math.min(buy2, p - sell1);
        sell2 = Math.max(sell2, p - buy2);
    }
    return sell2;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
