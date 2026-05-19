# LC 172 · Factorial Trailing Zeroes

| 項目 | 內容 |
|------|------|
| Pattern | Math |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/) |

**題意：** n! 尾端有幾個 0。

**核心：** 因子 5 的個數：`n/5 + n/25 + n/125 + ...`（2 比 5 多）。

```java
public int trailingZeroes(int n) {
    int count = 0;
    while (n > 0) {
        n /= 5;
        count += n;
    }
    return count;
}
```

**複雜度：** 時間 O(log n) · 空間 O(1)
