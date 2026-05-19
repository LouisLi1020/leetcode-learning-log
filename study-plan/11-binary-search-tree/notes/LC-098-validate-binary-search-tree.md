# LC 98 · Validate Binary Search Tree

| 項目 | 內容 |
|------|------|
| Pattern | DFS range |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/) |

**題意：** 驗證是否為合法 BST（左<根<右，遞迴定義）。

**核心：** DFS 帶 (min, max) 區間：node.val 須在 (min, max) 內；左右遞迴縮小界。

| 子樹 | 區間 |
|------|------|
| 左 | (min, node.val) |
| 右 | (node.val, max) |

```java
public boolean isValidBST(TreeNode root) {
    return valid(root, null, null);
}
boolean valid(TreeNode node, Integer min, Integer max) {
    if (node == null) return true;
    if ((min != null && node.val <= min) || (max != null && node.val >= max))
        return false;
    return valid(node.left, min, node.val)
        && valid(node.right, node.val, max);
}
```

**複雜度：** O(n) 時間，O(h) 空間。
