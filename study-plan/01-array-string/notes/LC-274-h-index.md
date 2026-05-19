# LC 274 · H-Index

| 項目 | 內容 |
|------|------|
| Pattern | Bucket sort |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [H-Index](https://leetcode.com/problems/h-index/) |

**題意：** H-Index：至少有 h 篇論文被引用 ≥ h 次，求最大 h。

**核心：** **桶排序**：citation≥n 放入 bucket[n]，由高到低累加找第一個 count≥i。

```java
public int hIndex(int[] citations) {
    int n = citations.length;
    int[] buckets = new int[n + 1];
    for (int c : citations) buckets[Math.min(c, n)]++;
    int count = 0;
    for (int i = n; i >= 0; i--) {
        count += buckets[i];
        if (count >= i) return i;
    }
    return 0;
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
