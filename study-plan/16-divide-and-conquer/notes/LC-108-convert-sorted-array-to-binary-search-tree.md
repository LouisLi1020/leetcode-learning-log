# LC 108 · Convert Sorted Array to Binary Search Tree

| 項目 | 內容 |
|------|------|
| Pattern | Divide |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/) |

**題意：** 將升序陣列轉成高度平衡的 BST。

**核心：** **分治：** 取中點 `mid` 為根，左半 `[l,mid)`、右半 `(mid,r)` 遞迴建子樹；中序即原順序。

```java
public TreeNode sortedArrayToBST(int[] nums) {
    return build(nums, 0, nums.length - 1);
}
TreeNode build(int[] nums, int l, int r) {
    if (l > r) return null;
    int mid = l + (r - l) / 2;
    TreeNode root = new TreeNode(nums[mid]);
    root.left = build(nums, l, mid - 1);
    root.right = build(nums, mid + 1, r);
    return root;
}
```

**複雜度：** 時間 O(n) · 空間 O(log n)（遞迴棧）
