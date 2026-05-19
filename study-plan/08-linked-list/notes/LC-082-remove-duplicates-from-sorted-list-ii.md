# LC 82 · Remove Duplicates from Sorted List II

| 項目 | 內容 |
|------|------|
| Pattern | Pointers |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/) |

**題意：** 已排序鏈結串列刪除所有重複節點（只保留不重複者）。

**核心：** dummy + **prev/cur**：若 cur 與下個同值則跳過整段重複。

```java
public ListNode deleteDuplicates(ListNode head) {
    ListNode dummy = new ListNode(0, head), prev = dummy;
    while (prev.next != null) {
        ListNode cur = prev.next;
        if (cur.next != null && cur.val == cur.next.val) {
            while (cur.next != null && cur.val == cur.next.val) cur = cur.next;
            prev.next = cur.next;
        } else prev = prev.next;
    }
    return dummy.next;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
