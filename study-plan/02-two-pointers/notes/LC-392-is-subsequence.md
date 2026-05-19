# LC 392 · Is Subsequence

| 項目 | 內容 |
|------|------|
| Pattern | Two pointers |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Is Subsequence](https://leetcode.com/problems/is-subsequence/) |

**題意：** s 是否為 t 的子序列（可不連續）。

**核心：** 雙指標掃 t，遇到等於 s[i] 則 i++，最後 i==s.length。

```java
public boolean isSubsequence(String s, String t) {
    int i = 0;
    for (char c : t.toCharArray()) {
        if (i < s.length() && s.charAt(i) == c) i++;
    }
    return i == s.length();
}
```

**複雜度：** 時間 O(|t|) · 空間 O(1)
