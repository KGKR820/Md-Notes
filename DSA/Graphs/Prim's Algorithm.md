- It is used to find the Minimum Spanning Tree of the given graph
- A MST is a subset of (V-1) edges that connect all vertices while minimising  the total edge weights sum
### Theory Style 
- Mark the start vertex as visited and add it into a subset (mstset).
- Now pick the vertex which is not visited and is connected to the vertices of the mstset then now find the edge having least edge weight among the edges connecting the non-visited vertices and the mstset vertices.
- Then add the edge to the MST graph and the vertex to mstset also make it visited
- Repeat this process until yo make all vertices visited.

### Coding Style
- Create a visited array with size of v(No.of vertices)  and assign all values to '0'.
- Now create a min-Heap which arranges the elements based on edge weight,so the min edge weight node always stays as the root node.
- Run a while loop until the min-Heap(priority queue) is empty.
- In the loop pop the top element(q) . If the q.vertex is already visited skip the loop if it is not visited then make vis[q.v] = 1 and loop through all the edges connected to q.v if the connected vertex has not been visited add that edge into the min-Heap but don't mark it as visited now.

```cpp
#include <bits/stdc++.h>
using namespace std;

// Modified to add edges in both directions for an undirected graph
void addEdge(vector<vector<pair<int, int>>> &Adj, int u, int v, int w) {
  Adj[u].push_back({v, w});
  Adj[v].push_back({u, w});
}

void Display(vector<vector<pair<int, int>>> &Adj) {
  for (int i = 0; i < Adj.size(); i++) {
    for (auto j : Adj[i]) {
      cout << i << " -> " << j.first << " : " << j.second << endl;
    }
  }
}

int Prims(vector<vector<pair<int, int>>> &Adj) {
  vector<int> vis(Adj.size(), 0);

  // Min Heap storing: {weight, parent_node, current_node}
  priority_queue<vector<int>, vector<vector<int>>, greater<vector<int>>> pq;

  // Start with weight 0, parent 0, current 0
  pq.push({0, 0, 0});
  int sum = 0;

  while (!pq.empty()) {
    vector<int> temp = pq.top();
    int wt = temp[0];
    int parent = temp[1];
    int curr = temp[2]; // This is the node we actually want to explore
    pq.pop();

    // Check if the CURRENT node is visited, not the parent
    if (vis[curr] == 1)
      continue;

    // Mark current node as visited
    vis[curr] = 1;
    sum += wt;

    // Print the edge (skip the initial dummy edge where parent == curr)
    if (parent != curr) {
      cout << "Edge " << parent << " -> " << curr << " : " << wt << "\n";
    }

    // Loop through the adjacent nodes of the CURRENT node
    for (int i = 0; i < Adj[curr].size(); i++) {
      int adjNode = Adj[curr][i].first;
      int edgeWt = Adj[curr][i].second;

      if (vis[adjNode] != 1) {
        // Push: {weight, current_node_as_parent, adjacent_node}
        pq.push({edgeWt, curr, adjNode});
      }
    }
  }
  return sum;
}

int main() {
  int n = 3;
  vector<vector<pair<int, int>>> Adj(n);

  // Adding undirected edges
  addEdge(Adj, 0, 1, 3);
  addEdge(Adj, 0, 2, 7);
  addEdge(Adj, 1, 2, 3);

  cout << "\nMinimum Spanning Tree Edges:\n";
  int mstWeight = Prims(Adj);
  cout << "Total MST Weight: " << mstWeight << "\n";

  return 0;
}
```

> Time Complexity : 
> Space Complexity : 