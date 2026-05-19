# LC 173 · Binary Search Tree Iterator

| 項目 | 內容 |
|------|------|
| Pattern | Stack |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Binary Search Tree Iterator](https://leetcode.com/problems/binary-search-tree-iterator/) |

**題意：** 設計 BST 迭代器，next() 回傳下一個最小值，均攤 O(1)。

**核心：** 中序 = 排序序；用 stack 模擬：一路 push 左鏈，next 彈 stack 頂再 push 其右子左鏈。

```java
class BSTIterator {
    Deque<TreeNode> stack = new ArrayDeque<>();

    public BSTIterator(TreeNode root) {
        pushLeft(root);
    }
    void pushLeft(TreeNode node) {
        while (node != null) { stack.push(node); node = node.left; }
    }
    public int next() {
        TreeNode cur = stack.pop();
        pushLeft(cur.right);
        return cur.val;
    }
    public boolean hasNext() { return !stack.isEmpty(); }
}
```

**複雜度：** 建構 O(h)；next/hasNext 均攤 O(1)；空間 O(h)。
