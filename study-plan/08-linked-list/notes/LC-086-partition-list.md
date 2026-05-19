# LC 86 · Partition List

| 項目 | 內容 |
|------|------|
| Pattern | Two lists |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Partition List](https://leetcode.com/problems/partition-list/) |

**題意：** 小於 x 的節點在前，其餘在後，保持相對順序。

**核心：** 兩條鏈 **before/after**，最後 before.tail 接 after.head。

```java
public ListNode partition(ListNode head, int x) {
    ListNode before = new ListNode(0), after = new ListNode(0);
    ListNode b = before, a = after;
    for (ListNode cur = head; cur != null; cur = cur.next) {
        if (cur.val < x) { b.next = cur; b = b.next; }
        else { a.next = cur; a = a.next; }
    }
    a.next = null;
    b.next = after.next;
    return before.next;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
