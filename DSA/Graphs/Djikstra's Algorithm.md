- This is used to find the shortest distance between a source node to all other nodes
- This is not applicable for negative cycle containing graphs (or) undirected graphs having negative weights as that shall cause the algorithm to loop infinitely in that negative loop to minimise the distance between the vertices.
- We shall use a min-heap to optimise the algo by picking the smallest edge.

```cpp
vector<int> Dj(vector<vector<int>> &Mat, int s) {
  int n = Mat.size();
  priority_queue<pair<int, int>, vector<pair<int, int>>,
                 greater<pair<int, int>>>
      pq;
  vector<int> dist(n, INT_MAX);

  dist[s] = 0;
  pq.push({0, s});

  while (!pq.empty()) {
    int dis = pq.top().first;
    int node = pq.top().second;
    pq.pop();

    if (dis > dist[node])
      continue;

    for (int i = 0; i < n; i++) {
      if (Mat[node][i] != INT_MAX) {
        if (dis + Mat[node][i] < dist[i]) {
          dist[i] = dis + Mat[node][i];
          pq.push({dist[i], i});
        }
      }
    }
  }
  return dist;
}
```

![[Negative Cycle.svg]]

> Time Complexity :
> Space Complexity :