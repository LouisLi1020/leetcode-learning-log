# LC 28 · Find the Index of the First Occurrence in a String

| 項目 | 內容 |
|------|------|
| Pattern | String match |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/) |

**題意：** 在 haystack 找 needle 第一次出現位置，無則 -1。

**核心：** **KMP**：next 陣列記最長相同前後綴，不匹配時 j=next[j-1] 跳過已比對段。

```java
public int strStr(String haystack, String needle) {
    if (needle.isEmpty()) return 0;
    int[] next = buildNext(needle);
    int j = 0;
    for (int i = 0; i < haystack.length(); i++) {
        while (j > 0 && haystack.charAt(i) != needle.charAt(j))
            j = next[j - 1];
        if (haystack.charAt(i) == needle.charAt(j)) j++;
        if (j == needle.length()) return i - needle.length() + 1;
    }
    return -1;
}
private int[] buildNext(String p) {
    int[] next = new int[p.length()];
    int j = 0;
    for (int i = 1; i < p.length(); i++) {
        while (j > 0 && p.charAt(i) != p.charAt(j)) j = next[j - 1];
        if (p.charAt(i) == p.charAt(j)) j++;
        next[i] = j;
    }
    return next;
}
```

**複雜度：** 時間 O(n+m) · 空間 O(m)
