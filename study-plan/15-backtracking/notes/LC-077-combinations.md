# LC 77 · Combinations

| 項目 | 內容 |
|------|------|
| Pattern | Backtrack |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Combinations](https://leetcode.com/problems/combinations/) |

**題意：** 從 1..n 選 k 個數的所有組合。

**核心：** 回溯：start 遞增選數，path 長度 k 時收集；剪枝：剩餘不足 k-i 則停。

```java
public List<List<Integer>> combine(int n, int k) {
    List<List<Integer>> ans = new ArrayList<>();
    backtrack(1, n, k, new ArrayList<>(), ans);
    return ans;
}
void backtrack(int start, int n, int k, List<Integer> path, List<List<Integer>> ans) {
    if (path.size() == k) { ans.add(new ArrayList<>(path)); return; }
    for (int i = start; i <= n - (k - path.size()) + 1; i++) {
        path.add(i);
        backtrack(i + 1, n, k, path, ans);
        path.remove(path.size() - 1);
    }
}
```

**複雜度：** O(C(n,k)·k) 時間，O(k) 空間。
