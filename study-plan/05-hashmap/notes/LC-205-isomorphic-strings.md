# LC 205 · Isomorphic Strings

| 項目 | 內容 |
|------|------|
| Pattern | Hash map |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/) |

**題意：** 兩字串是否同構（一對一字元映射）。

**核心：** 雙向 **HashMap** s→t 與 t→s，衝突則 false。

```java
public boolean isIsomorphic(String s, String t) {
    if (s.length() != t.length()) return false;
    Map<Character, Character> m1 = new HashMap<>(), m2 = new HashMap<>();
    for (int i = 0; i < s.length(); i++) {
        char a = s.charAt(i), b = t.charAt(i);
        if (m1.putIfAbsent(a, b) != null && m1.get(a) != b) return false;
        if (m2.putIfAbsent(b, a) != null && m2.get(b) != a) return false;
    }
    return true;
}
```

**複雜度：** 時間 O(n) · 空間 O(Σ)
