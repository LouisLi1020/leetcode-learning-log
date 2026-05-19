# LC 189 · Rotate Array

| 項目 | 內容 |
|------|------|
| Pattern | Three reverses |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Rotate Array](https://leetcode.com/problems/rotate-array/) |

**題意：** 將陣列向右旋轉 k 次，in-place。

**核心：** **三次 reverse**：整段、前 k、後段（k %= n）。

```java
public void rotate(int[] nums, int k) {
    int n = nums.length;
    k %= n;
    reverse(nums, 0, n - 1);
    reverse(nums, 0, k - 1);
    reverse(nums, k, n - 1);
}
private void reverse(int[] a, int l, int r) {
    while (l < r) { int t = a[l]; a[l++] = a[r]; a[r--] = t; }
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
