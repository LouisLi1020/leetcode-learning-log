# LC 88 · Merge Sorted Array

| 項目 | 內容 |
|------|------|
| Pattern | Two pointers |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/) |

**題意：** 將兩個已排序陣列合併進 nums1（in-place），結果 non-decreasing。

**核心：** 從**尾端**雙指標比較目前最大元素，較大者填入 nums1 末尾，避免覆蓋未處理元素。

| 變數 | 意義 |
|------|------|
| p1 | nums1 有效尾 |
| p2 | nums2 尾 |
| p | nums1 下一格寫入位置 |

```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int p1 = m - 1, p2 = n - 1, p = m + n - 1;
    while (p2 >= 0) {
        if (p1 >= 0 && nums1[p1] > nums2[p2]) {
            nums1[p--] = nums1[p1--];
        } else {
            nums1[p--] = nums2[p2--];
        }
    }
}
```

**複雜度：** 時間 O(m+n) · 空間 O(1)
