# LC 290 · Word Pattern

| 項目 | 內容 |
|------|------|
| Pattern | Hash map |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Word Pattern](https://leetcode.com/problems/word-pattern/) |

**題意：** pattern 與 s 是否一一對應（以空白分單字）。

**核心：** 同 205，但 key 為 **pattern 字元**、value 為整個 word。

```java
public boolean wordPattern(String pattern, String s) {
    String[] words = s.split(" ");
    if (pattern.length() != words.length) return false;
    Map<Character, String> m1 = new HashMap<>();
    Map<String, Character> m2 = new HashMap<>();
    for (int i = 0; i < pattern.length(); i++) {
        char c = pattern.charAt(i);
        String w = words[i];
        if (m1.containsKey(c) && !m1.get(c).equals(w)) return false;
        if (m2.containsKey(w) && m2.get(w) != c) return false;
        m1.put(c, w); m2.put(w, c);
    }
    return true;
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
