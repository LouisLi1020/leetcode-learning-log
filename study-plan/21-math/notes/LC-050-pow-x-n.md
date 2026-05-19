# LC 50 · Pow(x, n)

| 項目 | 內容 |
|------|------|
| Pattern | Fast power |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Pow(x, n)](https://leetcode.com/problems/pow-x-n/) |

**題意：** 計算 `x^n`（n 可負）。

**核心：** **快速冪：** `n` 奇則乘 `x`，`x*=x`，`n>>=1`；負指數先轉正再倒數。

```java
public double myPow(double x, int n) {
    long N = n;
    if (N < 0) { x = 1 / x; N = -N; }
    double res = 1.0;
    while (N > 0) {
        if ((N & 1) == 1) res *= x;
        x *= x;
        N >>= 1;
    }
    return res;
}
```

**複雜度：** 時間 O(log |n|) · 空間 O(1)
