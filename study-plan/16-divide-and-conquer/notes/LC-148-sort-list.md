# LC 148 · Sort List

| 項目 | 內容 |
|------|------|
| Pattern | Merge sort |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Sort List](https://leetcode.com/problems/sort-list/) |

**題意：** 對鏈結串列做 O(n log n) 排序。

**核心：** **鏈結串列合併排序：** `findMid` 切半 → 遞迴排左右 → `merge` 兩條有序鏈。

| 步驟 | 作用 |
|------|------|
| slow/fast | 找中點前一格切斷 |
| merge | 雙指標接成新鏈 |

```java
public ListNode sortList(ListNode head) {
    if (head == null || head.next == null) return head;
    ListNode slow = head, fast = head, prev = null;
    while (fast != null && fast.next != null) {
        prev = slow;
        slow = slow.next;
        fast = fast.next.next;
    }
    prev.next = null;
    ListNode left = sortList(head), right = sortList(slow);
    return merge(left, right);
}
ListNode merge(ListNode a, ListNode b) {
    ListNode dummy = new ListNode(0), cur = dummy;
    while (a != null && b != null) {
        if (a.val <= b.val) { cur.next = a; a = a.next; }
        else { cur.next = b; b = b.next; }
        cur = cur.next;
    }
    cur.next = (a != null) ? a : b;
    return dummy.next;
}
```

**複雜度：** 時間 O(n log n) · 空間 O(log n)
