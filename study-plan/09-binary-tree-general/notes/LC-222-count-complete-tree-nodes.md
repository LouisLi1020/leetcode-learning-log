# LC 222 · Count Complete Tree Nodes

| 項目 | 內容 |
|------|------|
| Pattern | DFS / binary lifting |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/) |

**題意：** 計算完全二元樹節點總數（要求優於 O(n)）。

**核心：** 算左右子樹高度 hL/hR：相等 → 左子樹是完美樹，節點 `2^hL`；不等 → 遞迴左或右（必有一邊完美）。

```java
public int countNodes(TreeNode root) {
    if (root == null) return 0;
    int hL = leftHeight(root.left);
    int hR = rightHeight(root.right);
    if (hL == hR)
        return (1 << hL) + countNodes(root.right);
    return (1 << hR) + countNodes(root.left);
}
int leftHeight(TreeNode node) {
    int h = 0;
    while (node != null) { h++; node = node.left; }
    return h;
}
int rightHeight(TreeNode node) {
    int h = 0;
    while (node != null) { h++; node = node.right; }
    return h;
}
```

**複雜度：** O(log² n) 時間，O(h) 空間。
