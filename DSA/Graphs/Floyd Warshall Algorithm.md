- It is also one of the shortest distance finding algorithms but it finds the shortest distances between every pair of vertices possible unlike [[Bellman Ford Algorithm]]
- Here we shall find shortest distance between j and k via i which means j -> i then i -> k

```cpp
// if a -> b is not reacheable then assign value 1e9
void floyd(vector<vector<int>> &Mat) {
  int n = Mat.size();
  for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
      for (int k = 0; k < n; k++) {
        Mat[j][k] = min(Mat[j][k], Mat[j][i] + Mat[i][k]);
      }
    }
  }
  for (int i = 0; i < n; i++) {
    if (Mat[i][i] < 0) {
      cout << "Negative cycle is present";
    }
  }
}
```

> Time Complexity :
> Space Complexity :