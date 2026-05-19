# LC 23 · Merge k Sorted Lists

| 項目 | 內容 |
|------|------|
| Pattern | Divide + heap |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) |

**題意：** 合併 k 條升序鏈結串列。

**核心：** **分治合併：** 兩兩 `mergeTwoLists` 直到一條；或 **最小堆** 存各鏈頭，每次彈最小接結果。

堆解法：時間 O(N log k)，適合 k 很大。

```java
public ListNode mergeKLists(ListNode[] lists) {
    if (lists == null || lists.length == 0) return null;
    return divide(lists, 0, lists.length - 1);
}
ListNode divide(ListNode[] lists, int l, int r) {
    if (l == r) return lists[l];
    int mid = l + (r - l) / 2;
    ListNode a = divide(lists, l, mid), b = divide(lists, mid + 1, r);
    return mergeTwo(a, b);
}
ListNode mergeTwo(ListNode a, ListNode b) {
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

**複雜度：** 時間 O(N log k) · 空間 O(log k)（N 為總節點）
