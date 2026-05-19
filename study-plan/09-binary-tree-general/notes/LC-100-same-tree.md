# LC 100 · Same Tree

| 項目 | 內容 |
|------|------|
| Pattern | DFS |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Same Tree](https://leetcode.com/problems/same-tree/) |

**題意：** 判斷兩棵二元樹結構與值是否完全相同。

**核心：** 同步 DFS：兩邊皆 null → true；一邊 null 或值不同 → false；再比左右子樹。

```java
public boolean isSameTree(TreeNode p, TreeNode q) {
    if (p == null && q == null) return true;
    if (p == null || q == null || p.val != q.val) return false;
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
}
```

**複雜度：** O(n) 時間，O(h) 空間。
