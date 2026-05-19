# LC 21 · Merge Two Sorted Lists

| 項目 | 內容 |
|------|------|
| Pattern | Merge |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) |

**題意：** 合併兩個已排序鏈結串列。

**核心：** **dummy** 尾指標，比較兩頭較小者接上。

```java
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(0), tail = dummy;
    while (l1 != null && l2 != null) {
        if (l1.val <= l2.val) { tail.next = l1; l1 = l1.next; }
        else { tail.next = l2; l2 = l2.next; }
        tail = tail.next;
    }
    tail.next = (l1 != null) ? l1 : l2;
    return dummy.next;
}
```

**複雜度：** 時間 O(n+m) · 空間 O(1)
