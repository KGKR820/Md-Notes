- Longest common sub-sequence , in this we shall find the longest matching string in both strings s1 and s2.
- We shall use a 2D dp array to solve this.

```cpp
int LCS(string &s1, string &s2) {
  int n1 = s1.length();
  int n2 = s2.length();
  vector<vector<int>> dp(n2 + 1, vector<int>(n1 + 1));
  
  for (int i = 0; i < n2 + 1; i++) {
    dp[i][0] = 0;
  }
  for (int i = 0; i < n1 + 1; i++) {
    dp[0][i] = 0;
  }
  
  for (int i = 1; i < n2 + 1; i++) {
    for (int j = 1; j < n1 + 1; j++) {
      if (s2[i - 1] == s1[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1] + 1;
      } else {
        dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
      }
    }
  }
  return dp[n2][n1];
}
```

> Time Complexity :
> Space Complexity :

![[LCS.svg]]