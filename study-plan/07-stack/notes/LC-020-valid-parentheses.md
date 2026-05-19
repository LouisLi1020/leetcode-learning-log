# LC 20 · Valid Parentheses

| 項目 | 內容 |
|------|------|
| Pattern | Stack |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) |

**題意：** 括號字串是否有效（成對且順序正確）。

**核心：** **Stack**：左括號 push，右括號 pop 比對。

```java
public boolean isValid(String s) {
    Deque<Character> st = new ArrayDeque<>();
    Map<Character, Character> pair = Map.of(')', '(', ']', '[', '}', '{');
    for (char c : s.toCharArray()) {
        if (pair.containsKey(c)) {
            if (st.isEmpty() || st.pop() != pair.get(c)) return false;
        } else st.push(c);
    }
    return st.isEmpty();
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
