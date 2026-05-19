# LC 2 · Add Two Numbers

| 項目 | 內容 |
|------|------|
| Pattern | Linked list |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/) |

**題意：** 刪除鏈結串列倒數第 n 個節點。

**核心：** **dummy** + 快慢指標：快先走 n+1 步，再一起走，刪 slow.next。

```java
public ListNode removeNthFromEnd(ListNode head, int n) {
    ListNode dummy = new ListNode(0, head);
    ListNode slow = dummy, fast = dummy;
    for (int i = 0; i <= n; i++) fast = fast.next;
    while (fast != null) { slow = slow.next; fast = fast.next; }
    slow.next = slow.next.next;
    return dummy.next;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
