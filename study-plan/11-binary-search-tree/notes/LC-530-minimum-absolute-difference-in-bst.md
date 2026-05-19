# LC 530 · Minimum Absolute Difference in BST

| 項目 | 內容 |
|------|------|
| Pattern | Inorder |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst/) |

**題意：** BST 中任意兩節點的最小絕對差。

**核心：** 中序遍歷得升序序列；相鄰差最小即答案。維護 prev 節點 O(1) 空間。

```java
int minDiff = Integer.MAX_VALUE;
TreeNode prev = null;

public int getMinimumDifference(TreeNode root) {
    inorder(root);
    return minDiff;
}
void inorder(TreeNode node) {
    if (node == null) return;
    inorder(node.left);
    if (prev != null)
        minDiff = Math.min(minDiff, node.val - prev.val);
    prev = node;
    inorder(node.right);
}
```

**複雜度：** O(n) 時間，O(h) 空間。
