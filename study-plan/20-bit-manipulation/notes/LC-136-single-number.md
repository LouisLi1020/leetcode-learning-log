# LC 136 · Single Number

| 項目 | 內容 |
|------|------|
| Pattern | XOR |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Single Number](https://leetcode.com/problems/single-number/) |

**題意：** 陣列中恰一個數出現一次，其餘兩次，找該數。

**核心：** 全部 **XOR**：`a^a=0`，`x^0=x`。

```java
public int singleNumber(int[] nums) {
    int x = 0;
    for (int n : nums) x ^= n;
    return x;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
