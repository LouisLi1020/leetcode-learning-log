# LC 39 · Combination Sum

| 項目 | 內容 |
|------|------|
| Pattern | Backtrack |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Combination Sum](https://leetcode.com/problems/combination-sum/) |

**題意：** candidates 無重複正整數，找所有和為 target 的組合（可重複用同一數）。

**核心：** 回溯：同 77 但可重複選 i（從 i 而非 i+1 遞迴）；sum>target 剪枝。

```java
public List<List<Integer>> combinationSum(int[] candidates, int target) {
    List<List<Integer>> ans = new ArrayList<>();
    backtrack(candidates, target, 0, new ArrayList<>(), 0, ans);
    return ans;
}
void backtrack(int[] nums, int target, int start, List<Integer> path, int sum,
               List<List<Integer>> ans) {
    if (sum == target) { ans.add(new ArrayList<>(path)); return; }
    if (sum > target) return;
    for (int i = start; i < nums.length; i++) {
        path.add(nums[i]);
        backtrack(nums, target, i, path, sum + nums[i], ans);
        path.remove(path.size() - 1);
    }
}
```

**複雜度：** 指數級時間，O(target) 遞迴深度。
