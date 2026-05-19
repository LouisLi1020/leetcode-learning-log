# LC 14 · Longest Common Prefix

| 項目 | 內容 |
|------|------|
| Pattern | String compare |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/) |

**題意：** 字串陣列最長公共前綴。

**核心：** 以 **第一個字串** 為基準，逐字比對其他字串同位置，不符即截斷。

```java
public String longestCommonPrefix(String[] strs) {
    if (strs.length == 0) return "";
    String prefix = strs[0];
    for (int i = 1; i < strs.length; i++) {
        while (!strs[i].startsWith(prefix)) {
            prefix = prefix.substring(0, prefix.length() - 1);
            if (prefix.isEmpty()) return "";
        }
    }
    return prefix;
}
```

**複雜度：** 時間 O(S) · 空間 O(1)
