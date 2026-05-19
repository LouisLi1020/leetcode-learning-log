# LC 236 · Lowest Common Ancestor of a Binary Tree

| 項目 | 內容 |
|------|------|
| Pattern | DFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) |

**題意：** 求二元樹中兩節點 p、q 的最低共同祖先（LCA）。

**核心：** 後序 DFS：若 node==p/q 回 node；左右皆非 null → node 即 LCA；否則回非 null 那邊。

```java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) return root;
    TreeNode left = lowestCommonAncestor(root.left, p, q);
    TreeNode right = lowestCommonAncestor(root.right, p, q);
    if (left != null && right != null) return root;
    return left != null ? left : right;
}
```

**複雜度：** O(n) 時間，O(h) 空間。
