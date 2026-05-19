# LC 128 · Longest Consecutive Sequence

| 項目 | 內容 |
|------|------|
| Pattern | Hash set |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) |

**題意：** 最長連續整數序列長度（O(n)）。

**核心：** 放入 Set；只從 **序列起點** num-1 不存在時往右擴展。

```java
public int longestConsecutive(int[] nums) {
    Set<Integer> set = new HashSet<>();
    for (int n : nums) set.add(n);
    int best = 0;
    for (int n : set) {
        if (!set.contains(n - 1)) {
            int len = 1, cur = n + 1;
            while (set.contains(cur)) { len++; cur++; }
            best = Math.max(best, len);
        }
    }
    return best;
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
