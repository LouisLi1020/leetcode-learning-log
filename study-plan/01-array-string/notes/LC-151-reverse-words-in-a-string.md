# LC 151 · Reverse Words in a String

| 項目 | 內容 |
|------|------|
| Pattern | Two pointers |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/) |

**題意：** 反轉字串中單字順序，去除多餘空白。

**核心：** **trim → split → 由尾往前拼接** 單字（中間單一空白）。

```java
public String reverseWords(String s) {
    String[] words = s.trim().split("\s+");
    StringBuilder sb = new StringBuilder();
    for (int i = words.length - 1; i >= 0; i--) {
        sb.append(words[i]);
        if (i > 0) sb.append(' ');
    }
    return sb.toString();
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
