# LC 58 · Length of Last Word

| 項目 | 內容 |
|------|------|
| Pattern | String |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Length of Last Word](https://leetcode.com/problems/length-of-last-word/) |

**題意：** 回傳字串最後一個單字的長度（尾端可有空白）。

**核心：** 從尾跳過空白，再往前直到空白，計算長度。

```java
public int lengthOfLastWord(String s) {
    int i = s.length() - 1;
    while (i >= 0 && s.charAt(i) == ' ') i--;
    int end = i;
    while (i >= 0 && s.charAt(i) != ' ') i--;
    return end - i;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
