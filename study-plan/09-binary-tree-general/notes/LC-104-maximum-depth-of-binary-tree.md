# LC 104 · Maximum Depth of Binary Tree

| 項目 | 內容 |
|------|------|
| Pattern | DFS/BFS |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) |

**題意：** 求二元樹最大深度（根到最遠葉的節點數）。

**核心：** 遞迴：空樹 0；否則 1 + max(左深, 右深)。也可 BFS 層序計層數。

```java
public int maxDepth(TreeNode root) {
    if (root == null) return 0;
    return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
}
```

**複雜度：** O(n) 時間，O(h) 空間（遞迴棧，h=樹高）。
