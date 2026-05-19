# LC 4 · Median of Two Sorted Arrays

| 項目 | 內容 |
|------|------|
| Pattern | Binary search partition |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/) |

**題意：** 兩個升序陣列的中位數。

**核心：** 在較短陣列上二分分割點 `i`，使左半總長 `(m+n+1)/2` 且 `maxLeft ≤ minRight`；否則移動 `i`。

| 變數 | 意義 |
|------|------|
| i | A 左半長度 |
| j | (m+n+1)/2 - i |
| 條件 | A[i-1]≤B[j] 且 B[j-1]≤A[i] |

```java
public double findMedianSortedArrays(int[] A, int[] B) {
    if (A.length > B.length) return findMedianSortedArrays(B, A);
    int m = A.length, n = B.length;
    int lo = 0, hi = m;
    while (lo <= hi) {
        int i = (lo + hi) / 2, j = (m + n + 1) / 2 - i;
        int aLeft = (i == 0) ? Integer.MIN_VALUE : A[i - 1];
        int aRight = (i == m) ? Integer.MAX_VALUE : A[i];
        int bLeft = (j == 0) ? Integer.MIN_VALUE : B[j - 1];
        int bRight = (j == n) ? Integer.MAX_VALUE : B[j];
        if (aLeft <= bRight && bLeft <= aRight) {
            if ((m + n) % 2 == 1) return Math.max(aLeft, bLeft);
            return (Math.max(aLeft, bLeft) + Math.min(aRight, bRight)) / 2.0;
        } else if (aLeft > bRight) hi = i - 1;
        else lo = i + 1;
    }
    return 0.0;
}
```

**複雜度：** 時間 O(log(min(m,n))) · 空間 O(1)
