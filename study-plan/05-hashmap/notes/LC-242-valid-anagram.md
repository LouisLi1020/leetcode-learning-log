# LC 242 · Valid Anagram

| 項目 | 內容 |
|------|------|
| Pattern | Counting |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Valid Anagram](https://leetcode.com/problems/valid-anagram/) |

**題意：** 兩字串是否為字母異位詞。

**核心：** 長度不同 false；**26 計數** 一增一減全為 0。

```java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) return false;
    int[] cnt = new int[26];
    for (int i = 0; i < s.length(); i++) {
        cnt[s.charAt(i) - 'a']++;
        cnt[t.charAt(i) - 'a']--;
    }
    for (int c : cnt) if (c != 0) return false;
    return true;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
