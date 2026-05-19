- Two strings are given s1 and s2 and now we should find the minimum of operations (insert,delete,replace a character) that should be done to convert s1 to s2.
- We shall use a 2D dp array to solve this problem.

```cpp
  string s1, s2;
  int n1 = s1.length();
  int n2 = s2.length();
  int dp[n2 + 1][n1 + 1];
  
  for (int i = 0; i < n1 + 1; i++) {
    dp[0][i] = i;
  }
  for (int i = 0; i < n2 + 1; i++) {
    dp[i][0] = i;
  }
  
  for (int i = 1; i < n2 + 1; i++) {
    for (int j = 1; j < n1 + 1; j++) {
    
      if (s2[i - 1] == s1[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1];
      } 
      else {
        dp[i][j] = 1 + min({dp[i - 1][j], dp[i][j - 1], dp[i - 1][j - 1]});
      }
    }
    
  }
  cout << "min :" << dp[n2][n1];
}
```

![[Edit Distance.svg|697]]

> Time Complexity :
> Space Complexity :