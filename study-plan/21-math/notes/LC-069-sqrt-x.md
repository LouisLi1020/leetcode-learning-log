# LC 69 · Sqrt(x)

| 項目 | 內容 |
|------|------|
| Pattern | Binary search |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Sqrt(x)](https://leetcode.com/problems/sqrt-x/) |

**題意：** 求 `sqrt(x)` 向下取整。

**核心：** 二分 `lo=0, hi=x`：若 `mid <= x/mid` 則答案至少 `mid`。

```java
public int mySqrt(int x) {
    if (x < 2) return x;
    int lo = 1, hi = x / 2;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if ((long) mid * mid <= x) lo = mid + 1;
        else hi = mid - 1;
    }
    return hi;
}
```

**複雜度：** 時間 O(log x) · 空間 O(1)
