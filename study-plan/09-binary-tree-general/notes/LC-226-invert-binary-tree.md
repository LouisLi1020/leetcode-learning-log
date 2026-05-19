# LC 226 · Invert Binary Tree

| 項目 | 內容 |
|------|------|
| Pattern | DFS |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/) |

**題意：** 鏡像翻轉整棵二元樹（左右子樹交換）。

**核心：** 後序或前序皆可：遞迴翻轉左右，再 swap(root.left, root.right)。

```java
public TreeNode invertTree(TreeNode root) {
    if (root == null) return null;
    TreeNode left = invertTree(root.left);
    TreeNode right = invertTree(root.right);
    root.left = right;
    root.right = left;
    return root;
}
```

**複雜度：** O(n) 時間，O(h) 空間。
