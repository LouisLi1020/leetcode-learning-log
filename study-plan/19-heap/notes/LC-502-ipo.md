# LC 502 · IPO

| 項目 | 內容 |
|------|------|
| Pattern | Heap + greedy |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [IPO](https://leetcode.com/problems/ipo/) |

**題意：** 最多 k 次投資、初始資本 w，最大化資本。

**核心：** 依 `capital` 排序；**最小堆** 存可投資的 `profit`，每次取最大利潤加入資本，重複 k 輪。

```java
public int findMaximizedCapital(int k, int w, int[] profits, int[] capital) {
    int n = capital.length;
    Integer[] idx = new Integer[n];
    for (int i = 0; i < n; i++) idx[i] = i;
    Arrays.sort(idx, (a, b) -> capital[a] - capital[b]);
    PriorityQueue<Integer> maxProfit = new PriorityQueue<>(Collections.reverseOrder());
    int i = 0;
    while (k-- > 0) {
        while (i < n && capital[idx[i]] <= w) {
            maxProfit.offer(profits[idx[i++]]);
        }
        if (maxProfit.isEmpty()) break;
        w += maxProfit.poll();
    }
    return w;
}
```

**複雜度：** 時間 O(n log n + k log n) · 空間 O(n)
