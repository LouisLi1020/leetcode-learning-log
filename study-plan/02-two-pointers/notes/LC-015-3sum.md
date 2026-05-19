# LC 15 · 3Sum

| 項目 | 內容 |
|------|------|
| Pattern | Sort + two pointers |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [3Sum](https://leetcode.com/problems/3sum/) |

**題意：** 找所有和為 0 的三元組（不重複）。

**核心：** 排序 + 固定 i，**l/r 雙指標**；和為 0 記錄後跳過重複。

```java
public List<List<Integer>> threeSum(int[] nums) {
    Arrays.sort(nums);
    List<List<Integer>> res = new ArrayList<>();
    for (int i = 0; i < nums.length - 2; i++) {
        if (i > 0 && nums[i] == nums[i - 1]) continue;
        int l = i + 1, r = nums.length - 1;
        while (l < r) {
            int sum = nums[i] + nums[l] + nums[r];
            if (sum == 0) {
                res.add(Arrays.asList(nums[i], nums[l], nums[r]));
                while (l < r && nums[l] == nums[l + 1]) l++;
                while (l < r && nums[r] == nums[r - 1]) r--;
                l++; r--;
            } else if (sum < 0) l++; else r--;
        }
    }
    return res;
}
```

**複雜度：** 時間 O(n²) · 空間 O(1) 不含輸出
