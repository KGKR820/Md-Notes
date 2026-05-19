- In this first we shall sort the edges in ascending order and add them one by one if both the ultimate parents of nodes are different 
- If the ultimate parents of both nodes is same we will not add that to MST.
- To check the condition properly and efficiently we shall use a disjoint set based on union size with path compression for finding the parent.

```cpp
struct DST { // Disjoint Set 
  vector<int> parent, sz;

  DST(int n) {
    parent.resize(n);
    sz.assign(n, 1);

    for (int i = 0; i < parent.size(); i++) {
      parent[i] = i;
    }
  }
  
  int findparent(int v) {
    if (parent[v] == v)
      return v;

    return parent[v] = findparent(parent[v]); // Path Compression
  }
  
  bool connect(int a, int b) {
    int pa = findparent(a);
    int pb = findparent(b);
	
    if (pa != pb) {
	// Always connect small size parent node to big size parent node 
      if (sz[pa] < sz[pb]) {
        sz[pb] += sz[pa];
        parent[pa] = pb;
      } else {
        sz[pa] += sz[pb];
        parent[pb] = pa;
      }
      return true;
    }
    return false;
  }
};

vector<pair<int, pair<int, int>>> Krushkal(vector<vector<int>> &mat) {
  int n = mat.size();
  DST DS = DST(n);
  vector<pair<int, pair<int, int>>> sub, output;

  for (int i = 0; i < n; i++) {
    for (int j = i + 1; j < n; j++) {
      if (mat[i][j] != INT_MAX) {
        sub.push_back({mat[i][j], {i, j}});
      }
    }
  }

  sort(sub.begin(), sub.end());

  for (int i = 0; i < sub.size(); i++) {
    if (DS.connect(sub[i].second.second, sub[i].second.first)) {
      output.push_back(sub[i]);
    }
  }
  return output;
}

```

## Personal Note :

![[Krushkal note.png]]

> Time Complexity :
> Space Complexity :