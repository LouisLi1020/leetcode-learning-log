# LC 134 · Gas Station

| 項目 | 內容 |
|------|------|
| Pattern | Greedy circuit |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Gas Station](https://leetcode.com/problems/gas-station/) |

**題意：** 環形加油站，gas[i] 加油 cost[i] 耗油，求唯一可行起點或 -1。

**核心：** 總油量 total≥0 才有解；**tank** 累積，若 tank<0 起點改 i+1 並清零。

```java
public int canCompleteCircuit(int[] gas, int[] cost) {
    int total = 0, tank = 0, start = 0;
    for (int i = 0; i < gas.length; i++) {
        int diff = gas[i] - cost[i];
        total += diff;
        tank += diff;
        if (tank < 0) { start = i + 1; tank = 0; }
    }
    return total >= 0 ? start : -1;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
