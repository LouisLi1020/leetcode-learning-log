# LC 137 · Single Number II

| 項目 | 內容 |
|------|------|
| Pattern | Bit count |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Single Number II](https://leetcode.com/problems/single-number-ii/) |

**題意：** 恰一個數出現一次，其餘三次，找該數。

**核心：** 統計每位 mod 3：`ones` 記出現 1 次、`twos` 記 2 次；進位式更新。

```java
public int singleNumber(int[] nums) {
    int ones = 0, twos = 0;
    for (int n : nums) {
        ones = (ones ^ n) & ~twos;
        twos = (twos ^ n) & ~ones;
    }
    return ones;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
