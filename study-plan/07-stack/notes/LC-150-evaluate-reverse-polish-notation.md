# LC 150 · Evaluate Reverse Polish Notation

| 項目 | 內容 |
|------|------|
| Pattern | Stack |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/) |

**題意：** 逆波蘭表示法求值（+ - * /）。

**核心：** 遇數字 push，遇運算子 pop 兩個計算再 push。

```java
public int evalRPN(String[] tokens) {
    Deque<Integer> st = new ArrayDeque<>();
    for (String t : tokens) {
        if (t.equals("+")) st.push(st.pop() + st.pop());
        else if (t.equals("-")) { int b = st.pop(), a = st.pop(); st.push(a - b); }
        else if (t.equals("*")) st.push(st.pop() * st.pop());
        else if (t.equals("/")) { int b = st.pop(), a = st.pop(); st.push(a / b); }
        else st.push(Integer.parseInt(t));
    }
    return st.pop();
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
