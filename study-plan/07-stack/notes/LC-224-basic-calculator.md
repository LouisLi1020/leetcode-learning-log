# LC 224 · Basic Calculator

| 項目 | 內容 |
|------|------|
| Pattern | Stack |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Basic Calculator](https://leetcode.com/problems/basic-calculator/) |

**題意：** 字串基本計算器：+ - 與括號，無乘除。

**核心：** Stack 存 **sign** 與累加；遇 ( 推入當前結果與符號，遇 ) 合併。

```java
public int calculate(String s) {
    Deque<Integer> stack = new ArrayDeque<>();
    int res = 0, num = 0, sign = 1;
    for (char c : s.toCharArray()) {
        if (Character.isDigit(c)) num = num * 10 + (c - '0');
        else if (c == '+' || c == '-') {
            res += sign * num; num = 0; sign = (c == '+') ? 1 : -1;
        } else if (c == '(') {
            stack.push(res); stack.push(sign);
            res = 0; sign = 1;
        } else if (c == ')') {
            res += sign * num; num = 0;
            res *= stack.pop(); res += stack.pop();
        }
    }
    return res + sign * num;
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
