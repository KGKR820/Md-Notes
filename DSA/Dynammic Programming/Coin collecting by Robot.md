- In this problem we have a 2D matrix with coins placed on some locations , so now we should find the maximum amount it can bring top left to bottom right cell by only moving down and right only.

```cpp
int robot(vector<vector<int>> &Mat) {
  int n = Mat.size();
  int k = Mat[0].size();
  vector<vector<int>> dp(n, vector<int>(k));
  dp[0][0] = Mat[0][0];
  
  for (int i = 1; i < k; i++) {
    dp[0][i] = dp[0][i - 1] + Mat[0][i];
  }
  for (int i = 1; i < n; i++) {
    dp[i][0] = dp[i - 1][0] + Mat[i][0];
  }
  
  for (int i = 1; i < n; i++) {
    for (int j = 1; j < k; j++) {
      dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]) + Mat[i][j];
    }
  }
  
  return dp[n - 1][k - 1];
}
```

> Time Complexity :
> Space Complexity :

![[Robot_coin.png]]
