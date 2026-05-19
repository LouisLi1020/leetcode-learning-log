# LC 46 · Permutations

| 項目 | 內容 |
|------|------|
| Pattern | Backtrack |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Permutations](https://leetcode.com/problems/permutations/) |

**題意：** 陣列 nums 全排列（無重複）。

**核心：** 回溯 + used[]：path 滿長度收集；每輪選未使用的數。

```java
public List<List<Integer>> permute(int[] nums) {
    List<List<Integer>> ans = new ArrayList<>();
    backtrack(nums, new boolean[nums.length], new ArrayList<>(), ans);
    return ans;
}
void backtrack(int[] nums, boolean[] used, List<Integer> path, List<List<Integer>> ans) {
    if (path.size() == nums.length) { ans.add(new ArrayList<>(path)); return; }
    for (int i = 0; i < nums.length; i++) {
        if (used[i]) continue;
        used[i] = true;
        path.add(nums[i]);
        backtrack(nums, used, path, ans);
        path.remove(path.size() - 1);
        used[i] = false;
    }
}
```

**複雜度：** O(n·n!) 時間，O(n) 空間。
