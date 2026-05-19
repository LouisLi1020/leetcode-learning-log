# LC 452 · Minimum Number of Arrows to Burst Balloons

| 項目 | 內容 |
|------|------|
| Pattern | Greedy |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/) |

**題意：** 最多氣球用最少箭（區間 [xend]）。

**核心：** 按 **end 排序**；貪心：若 start>lastEnd 需新箭並更新 end。

```java
public int findMinArrowShots(int[][] points) {
    Arrays.sort(points, (a, b) -> Integer.compare(a[1], b[1]));
    int arrows = 0, lastEnd = Integer.MIN_VALUE;
    for (int[] p : points) {
        if (p[0] > lastEnd) { arrows++; lastEnd = p[1]; }
    }
    return arrows;
}
```

**複雜度：** 時間 O(n log n) · 空間 O(1)
