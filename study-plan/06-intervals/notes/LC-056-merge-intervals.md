# LC 56 · Merge Intervals

| 項目 | 內容 |
|------|------|
| Pattern | Sort + merge |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Merge Intervals](https://leetcode.com/problems/merge-intervals/) |

**題意：** 合併所有重疊區間。

**核心：** 按起點排序；若 curr.start<=prev.end 則擴展 end，否則加入結果。

```java
public int[][] merge(int[][] intervals) {
    Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
    List<int[]> merged = new ArrayList<>();
    for (int[] iv : intervals) {
        if (merged.isEmpty() || iv[0] > merged.get(merged.size()-1)[1])
            merged.add(iv);
        else
            merged.get(merged.size()-1)[1] = Math.max(merged.get(merged.size()-1)[1], iv[1]);
    }
    return merged.toArray(new int[merged.size()][]);
}
```

**複雜度：** 時間 O(n log n) · 空間 O(n)
