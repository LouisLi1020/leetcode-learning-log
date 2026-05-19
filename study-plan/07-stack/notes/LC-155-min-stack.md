# LC 155 · Min Stack

| 項目 | 內容 |
|------|------|
| Pattern | Design |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Min Stack](https://leetcode.com/problems/min-stack/) |

**題意：** 實作 Min Stack：push/pop/top/getMin 均 O(1)。

**核心：** 兩個 stack：資料棧 + **同步最小值棧**。

```java
class MinStack {
    private final Deque<Integer> stack = new ArrayDeque<>();
    private final Deque<Integer> mins = new ArrayDeque<>();
    public void push(int val) {
        stack.push(val);
        mins.push(mins.isEmpty() ? val : Math.min(val, mins.peek()));
    }
    public void pop() { stack.pop(); mins.pop(); }
    public int top() { return stack.peek(); }
    public int getMin() { return mins.peek(); }
}
```

**複雜度：** 各操作 O(1) · 空間 O(n)
