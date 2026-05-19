# LC 383 · Ransom Note

| 項目 | 內容 |
|------|------|
| Pattern | Counting |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Ransom Note](https://leetcode.com/problems/ransom-note/) |

**題意：** 能否用 magazine 字母拼出 ransomNote（每字元用量有限）。

**核心：** 統計 magazine 字頻，逐字扣減，不足則 false。

```java
public boolean canConstruct(String ransomNote, String magazine) {
    int[] cnt = new int[26];
    for (char c : magazine.toCharArray()) cnt[c - 'a']++;
    for (char c : ransomNote.toCharArray()) {
        if (--cnt[c - 'a'] < 0) return false;
    }
    return true;
}
```

**複雜度：** 時間 O(m+n) · 空間 O(1)
