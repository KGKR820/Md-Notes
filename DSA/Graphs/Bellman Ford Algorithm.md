- Similar to [[Djikstra's Algorithm]] , Bellman Ford algo is used to find the shortest distance between a source node and all other nodes
- But by using this we can detect if a negative cycle is present or not.
- We shall fill the shortest distance array by doing n-1 relaxation cycles where n is no.of vertices and during each relaxation we shall find the shortest distances by using previous relaxation output.

```cpp
vector<int> Bellman(int n, vector<vector<int>> &list, int s) {
  const int INF = 1e9; // Safe infinity
  vector<int> dist(n, INF);
  dist[s] = 0;

  for (int i = 0; i < n - 1; i++) {
    for (int j = 0; j < list.size(); j++) {
      int wt = list[j][0];
      int node1 = list[j][1];
      int node2 = list[j][2];

      if (dist[node1] != INF && dist[node1] + wt < dist[node2]) {
        dist[node2] = dist[node1] + wt;
      }
    }
  }

  // Nth Relaxation to check -ve cycles
  for (int j = 0; j < list.size(); j++) {
    int wt = list[j][0];
    int node1 = list[j][1];
    int node2 = list[j][2];

    if (dist[node1] != INF && dist[node1] + wt < dist[node2]) {
      cout << "Negative Cycle is present";
      return {-1};
    }
  }

  return dist;
}

```

> Time Complexity :
> Space Complexity :