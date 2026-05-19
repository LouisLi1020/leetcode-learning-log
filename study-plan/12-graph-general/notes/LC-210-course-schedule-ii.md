# LC 210 · Course Schedule II

| 項目 | 內容 |
|------|------|
| Pattern | Topo sort |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/) |

**題意：** 回傳修完所有課的一種拓撲順序；不可能則空陣列。

**核心：** 同 207 Kahn BFS，依出隊順序收集即答案。

```java
public int[] findOrder(int numCourses, int[][] prerequisites) {
    int[] indeg = new int[numCourses];
    List<List<Integer>> adj = new ArrayList<>();
    for (int i = 0; i < numCourses; i++) adj.add(new ArrayList<>());
    for (int[] p : prerequisites) {
        adj.get(p[1]).add(p[0]);
        indeg[p[0]]++;
    }
    Queue<Integer> q = new ArrayDeque<>();
    for (int i = 0; i < numCourses; i++)
        if (indeg[i] == 0) q.offer(i);
    int[] order = new int[numCourses];
    int idx = 0;
    while (!q.isEmpty()) {
        int u = q.poll();
        order[idx++] = u;
        for (int v : adj.get(u))
            if (--indeg[v] == 0) q.offer(v);
    }
    return idx == numCourses ? order : new int[0];
}
```

**複雜度：** O(V+E) 時間，O(V+E) 空間。
