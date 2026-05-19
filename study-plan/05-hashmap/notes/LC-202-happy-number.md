# LC 202 · Happy Number

| 項目 | 內容 |
|------|------|
| Pattern | Cycle detection |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Happy Number](https://leetcode.com/problems/happy-number/) |

**題意：** 反覆將 n 換成各位平方和，是否進入 1。

**核心：** HashSet 記已見值；循環中若為 1 回 true，重複回 false。

```java
public boolean isHappy(int n) {
    Set<Integer> seen = new HashSet<>();
    while (n != 1 && seen.add(n)) {
        int sum = 0;
        while (n > 0) {
            int d = n % 10;
            sum += d * d;
            n /= 10;
        }
        n = sum;
    }
    return n == 1;
}
```

**複雜度：** 時間 O(log n) · 空間 O(log n)
