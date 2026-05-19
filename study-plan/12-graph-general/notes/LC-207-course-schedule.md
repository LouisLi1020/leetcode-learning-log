# LC 207 · Course Schedule

| 項目 | 內容 |
|------|------|
| Pattern | Topo sort |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Course Schedule](https://leetcode.com/problems/course-schedule/) |

**題意：** 課程與先修關係，能否修完所有課（無循環依賴）。

**核心：** Kahn 拓撲排序：建入度表 + adjacency；入度 0 入隊，逐個消去邊；處理數==numCourses 即可。

```java
public boolean canFinish(int numCourses, int[][] prerequisites) {
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
    int taken = 0;
    while (!q.isEmpty()) {
        int u = q.poll();
        taken++;
        for (int v : adj.get(u))
            if (--indeg[v] == 0) q.offer(v);
    }
    return taken == numCourses;
}
```

**複雜度：** O(V+E) 時間，O(V+E) 空間。
