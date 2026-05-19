# LC 19 · Remove Nth Node From End of List

| 項目 | 內容 |
|------|------|
| Pattern | Two pointers |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) |

**題意：** 刪除倒數第 n 個節點（同 LC2）。

**核心：** dummy + 快指標先走 n+1 步，再同步走並刪除 slow.next。

```java
public ListNode removeNthFromEnd(ListNode head, int n) {
    ListNode dummy = new ListNode(0, head), slow = dummy, fast = dummy;
    for (int i = 0; i <= n; i++) fast = fast.next;
    while (fast != null) { slow = slow.next; fast = fast.next; }
    slow.next = slow.next.next;
    return dummy.next;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
