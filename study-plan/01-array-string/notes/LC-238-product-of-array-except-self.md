# LC 238 · Product of Array Except Self

| 項目 | 內容 |
|------|------|
| Pattern | Prefix/suffix product |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) |

**題意：** 原地將陣列按 0、1、2 排序（荷蘭國旗）。

**核心：** **三指標** low/mid/high：mid==1 交換後 mid++；mid==2 與 high 交換僅 high--。

```java
public void sortColors(int[] nums) {
    int low = 0, mid = 0, high = nums.length - 1;
    while (mid <= high) {
        if (nums[mid] == 0) {
            swap(nums, low++, mid++);
        } else if (nums[mid] == 1) {
            mid++;
        } else {
            swap(nums, mid, high--);
        }
    }
}
private void swap(int[] a, int i, int j) { int t = a[i]; a[i] = a[j]; a[j] = t; }
```

**複雜度：** 時間 O(n) · 空間 O(1)
