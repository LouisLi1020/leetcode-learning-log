# LC 105 · Construct Binary Tree from Preorder and Inorder Traversal

| 項目 | 內容 |
|------|------|
| Pattern | Divide |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/) |

**題意：** 給 preorder + inorder，重建唯一二元樹。

**核心：** preorder[0] 是根；在 inorder 找根位置切左右子區間；遞迴建子樹。用 HashMap 存 inorder 索引加速。

| 步驟 | 動作 |
|------|------|
| 1 | rootVal = preorder[preL] |
| 2 | mid = inIndex[rootVal] |
| 3 | 左大小 = mid - inL，切 preorder/inorder 區間遞迴 |

```java
int preIdx;
Map<Integer, Integer> idx = new HashMap<>();

public TreeNode buildTree(int[] preorder, int[] inorder) {
    for (int i = 0; i < inorder.length; i++) idx.put(inorder[i], i);
    preIdx = 0;
    return build(preorder, 0, inorder.length - 1);
}
TreeNode build(int[] pre, int inL, int inR) {
    if (inL > inR) return null;
    int rootVal = pre[preIdx++];
    TreeNode root = new TreeNode(rootVal);
    int mid = idx.get(rootVal);
    root.left = build(pre, inL, mid - 1);
    root.right = build(pre, mid + 1, inR);
    return root;
}
```

**複雜度：** O(n) 時間，O(n) 空間（map + 遞迴棧）。
