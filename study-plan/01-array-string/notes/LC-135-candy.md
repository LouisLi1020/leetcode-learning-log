# LC 135 · Candy

| 項目 | 內容 |
|------|------|
| Pattern | Greedy two-pass |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Candy](https://leetcode.com/problems/candy/) |

**題意：** 評分比鄰居高才得糖，每人至少 1 顆，求最少糖果總數。

**核心：** 兩趟：**左→右** 遞增則+1；**右→左** 再與右鄰比取 max，累加 candies。

```java
public int candy(int[] ratings) {
    int n = ratings.length;
    int[] candies = new int[n];
    Arrays.fill(candies, 1);
    for (int i = 1; i < n; i++)
        if (ratings[i] > ratings[i - 1]) candies[i] = candies[i - 1] + 1;
    for (int i = n - 2; i >= 0; i--)
        if (ratings[i] > ratings[i + 1])
            candies[i] = Math.max(candies[i], candies[i + 1] + 1);
    int sum = 0;
    for (int c : candies) sum += c;
    return sum;
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
