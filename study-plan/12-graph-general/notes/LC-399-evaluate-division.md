# LC 399 · Evaluate Division

| 項目 | 內容 |
|------|------|
| Pattern | Union-find / graph |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Evaluate Division](https://leetcode.com/problems/evaluate-division/) |

**題意：** 除法 queries：`a/b=val` 已知，求 `x/y`；無解回 -1。

**核心：** 建無向加權圖（a→b 權 val，b→a 權 1/val）；每個 query DFS/BFS 找路徑乘積。

```java
public double[] calcEquation(
        List<List<String>> equations, double[] values, List<List<String>> queries) {
    Map<String, Map<String, Double>> g = new HashMap<>();
    for (int i = 0; i < equations.size(); i++) {
        String a = equations.get(i).get(0), b = equations.get(i).get(1);
        g.computeIfAbsent(a, k -> new HashMap<>()).put(b, values[i]);
        g.computeIfAbsent(b, k -> new HashMap<>()).put(a, 1.0 / values[i]);
    }
    double[] ans = new double[queries.size()];
    for (int i = 0; i < queries.size(); i++) {
        String src = queries.get(i).get(0), dst = queries.get(i).get(1);
        if (!g.containsKey(src) || !g.containsKey(dst)) ans[i] = -1.0;
        else {
            Set<String> seen = new HashSet<>();
            ans[i] = dfs(g, src, dst, 1.0, seen);
        }
    }
    return ans;
}
double dfs(Map<String, Map<String, Double>> g, String cur, String dst,
           double prod, Set<String> seen) {
    if (cur.equals(dst)) return prod;
    seen.add(cur);
    for (var e : g.get(cur).entrySet()) {
        if (!seen.contains(e.getKey())) {
            double res = dfs(g, e.getKey(), dst, prod * e.getValue(), seen);
            if (res != -1.0) return res;
        }
    }
    return -1.0;
}
```

**複雜度：** O(Q·(V+E)) 時間，O(V) 空間。
