# LC 201 · Bitwise AND of Numbers Range

| 項目 | 內容 |
|------|------|
| Pattern | Bit |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/) |

**題意：** 求區間 `[left, right]` 內所有數的 AND。

**核心：** 共同高位相同：右移直到 `left==right`，再左移回原位數。

```java
public int rangeBitwiseAnd(int left, int right) {
    int shift = 0;
    while (left < right) {
        left >>= 1;
        right >>= 1;
        shift++;
    }
    return left << shift;
}
```

**複雜度：** 時間 O(1)（位數固定）· 空間 O(1)
