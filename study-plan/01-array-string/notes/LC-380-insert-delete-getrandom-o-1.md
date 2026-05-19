# LC 380 · Insert Delete GetRandom O(1)

| 項目 | 內容 |
|------|------|
| Pattern | HashMap + list |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o-1/) |

**題意：** 設計結構：insert/remove/getRandom 平均 O(1)。

**核心：** **ArrayList + HashMap**：list 存值、map 存 index；刪除時與尾元素交換再 pop。

```java
class RandomizedSet {
    private final List<Integer> list = new ArrayList<>();
    private final Map<Integer, Integer> idx = new HashMap<>();
    public boolean insert(int val) {
        if (idx.containsKey(val)) return false;
        idx.put(val, list.size());
        list.add(val);
        return true;
    }
    public boolean remove(int val) {
        if (!idx.containsKey(val)) return false;
        int i = idx.get(val), last = list.get(list.size() - 1);
        list.set(i, last);
        idx.put(last, i);
        list.remove(list.size() - 1);
        idx.remove(val);
        return true;
    }
    public int getRandom() {
        return list.get((int)(Math.random() * list.size()));
    }
}
```

**複雜度：** 各操作均攤 O(1) · 空間 O(n)
