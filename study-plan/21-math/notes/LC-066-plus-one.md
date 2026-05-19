# LC 66 · Plus One

| 項目 | 內容 |
|------|------|
| Pattern | Array |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Plus One](https://leetcode.com/problems/plus-one/) |

**題意：** 大整數陣列 +1（最高位在索引 0）。

**核心：** 由尾往前進位；若全 9 則開頭補 1。

```java
public int[] plusOne(int[] digits) {
    for (int i = digits.length - 1; i >= 0; i--) {
        if (digits[i] < 9) {
            digits[i]++;
            return digits;
        }
        digits[i] = 0;
    }
    int[] res = new int[digits.length + 1];
    res[0] = 1;
    return res;
}
```

**複雜度：** 時間 O(n) · 空間 O(1) 或 O(n)（進位溢出）
