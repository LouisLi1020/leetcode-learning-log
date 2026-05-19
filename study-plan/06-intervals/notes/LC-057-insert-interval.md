# LC 57 · Insert Interval

| 項目 | 內容 |
|------|------|
| Pattern | Merge |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Insert Interval](https://leetcode.com/problems/insert-interval/) |

**題意：** 在無重疊已排序區間中插入 newInterval 並合併。

**核心：** 三階段：加入在前的、**合併重疊**、加入在後的。

```java
public int[][] insert(int[][] intervals, int[] newInterval) {
    List<int[]> res = new ArrayList<>();
    int i = 0, n = intervals.length;
    while (i < n && intervals[i][1] < newInterval[0]) res.add(intervals[i++]);
    while (i < n && intervals[i][0] <= newInterval[1]) {
        newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
        newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
        i++;
    }
    res.add(newInterval);
    while (i < n) res.add(intervals[i++]);
    return res.toArray(new int[res.size()][]);
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
