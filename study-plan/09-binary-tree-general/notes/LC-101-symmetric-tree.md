# LC 101 · Symmetric Tree

| 項目 | 內容 |
|------|------|
| Pattern | DFS |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/) |

**題意：** 判斷二元樹是否軸對稱（左子樹鏡像等於右子樹）。

**核心：** 拆成 mirror(a, b)：值相同且 a.left↔b.right、a.right↔b.left 遞迴成立。

```java
public boolean isSymmetric(TreeNode root) {
    return mirror(root, root);
}
boolean mirror(TreeNode a, TreeNode b) {
    if (a == null && b == null) return true;
    if (a == null || b == null || a.val != b.val) return false;
    return mirror(a.left, b.right) && mirror(a.right, b.left);
}
```

**複雜度：** O(n) 時間，O(h) 空間。
