# LC 5 · Longest Palindromic Substring

| 項目 | 內容 |
|------|------|
| Pattern | DP / expand |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) |

**題意：** 求最長回文子字串。

**核心：** **中心擴展：** 枚舉中心（單/雙字元），向兩側擴；或 DP `P[i][j]`。

```java
public String longestPalindrome(String s) {
    int start = 0, maxLen = 0;
    for (int i = 0; i < s.length(); i++) {
        int len1 = expand(s, i, i);
        int len2 = expand(s, i, i + 1);
        int len = Math.max(len1, len2);
        if (len > maxLen) {
            maxLen = len;
            start = i - (len - 1) / 2;
        }
    }
    return s.substring(start, start + maxLen);
}
int expand(String s, int l, int r) {
    while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
        l--; r++;
    }
    return r - l - 1;
}
```

**複雜度：** 時間 O(n²) · 空間 O(1)
