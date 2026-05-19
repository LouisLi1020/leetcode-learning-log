# LC 191 · Number of 1 Bits

| 項目 | 內容 |
|------|------|
| Pattern | Bit count |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/) |

**題意：** 計算 unsigned 整數中 1 的個數。

**核心：** `n &= n-1` 清除最低位 1，計數次數（Brian Kernighan）。

```java
public int hammingWeight(int n) {
    int count = 0;
    while (n != 0) {
        n &= (n - 1);
        count++;
    }
    return count;
}
```

**複雜度：** 時間 O(位數) · 空間 O(1)
