# LC 9 · Palindrome Number

| 項目 | 內容 |
|------|------|
| Pattern | Math |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Palindrome Number](https://leetcode.com/problems/palindrome-number/) |

**題意：** 判斷整數是否回文（不用字串）。

**核心：** 反轉後半段與前半比較；`x<0` 或尾 0 且非 0 直接 false。

```java
public boolean isPalindrome(int x) {
    if (x < 0 || (x % 10 == 0 && x != 0)) return false;
    int rev = 0;
    while (x > rev) {
        rev = rev * 10 + x % 10;
        x /= 10;
    }
    return x == rev || x == rev / 10;
}
```

**複雜度：** 時間 O(log x) · 空間 O(1)
