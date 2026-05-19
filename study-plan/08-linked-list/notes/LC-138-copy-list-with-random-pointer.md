# LC 138 · Copy List with Random Pointer

| 項目 | 內容 |
|------|------|
| Pattern | Hash / interleave |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/) |

**題意：** 複製帶 random 指標的鏈結串列。

**核心：** 兩遍：**old→new** HashMap，再連接 next 與 random。

```java
public Node copyRandomList(Node head) {
    if (head == null) return null;
    Map<Node, Node> map = new HashMap<>();
    for (Node cur = head; cur != null; cur = cur.next)
        map.put(cur, new Node(cur.val));
    for (Node cur = head; cur != null; cur = cur.next) {
        map.get(cur).next = map.get(cur.next);
        map.get(cur).random = map.get(cur.random);
    }
    return map.get(head);
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
