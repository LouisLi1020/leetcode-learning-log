# LC 190 · Reverse Bits

| 項目 | 內容 |
|------|------|
| Pattern | Bit |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Reverse Bits](https://leetcode.com/problems/reverse-bits/) |

**題意：** 反轉 32 位元無符號整數的二進位。

**核心：** 每次取最低位接到 `res` 左移；`n` 右移；共 32 次。

```java
public int reverseBits(int n) {
    int res = 0;
    for (int i = 0; i < 32; i++) {
        res = (res << 1) | (n & 1);
        n >>>= 1;
    }
    return res;
}
```

**複雜度：** 時間 O(1) · 空間 O(1)
