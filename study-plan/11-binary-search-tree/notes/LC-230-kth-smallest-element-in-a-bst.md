# LC 230 · Kth Smallest Element in a BST

| 項目 | 內容 |
|------|------|
| Pattern | Inorder |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) |

**題意：** BST 中第 k 小元素（1-indexed）。

**核心：** 中序遍歷：每訪問一節點 k--，k==0 即答案。

```java
int kth;
int ans;

public int kthSmallest(TreeNode root, int k) {
    kth = k;
    inorder(root);
    return ans;
}
void inorder(TreeNode node) {
    if (node == null || kth == 0) return;
    inorder(node.left);
    if (--kth == 0) ans = node.val;
    inorder(node.right);
}
```

**複雜度：** O(n) 時間，O(h) 空間；可 stack 迭代同複雜度。
