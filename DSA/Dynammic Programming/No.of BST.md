- In this problem we should calculate the number of unique BST using 1....n numbers
- We shall use a 1D dp array of size n+1 to store the outputs of i th values.

```cpp
int count(int n) {
  vector<int> dp(n + 1, 0);
  dp[0] = 1;
  dp[1] = 1;
  
  if (n <= 1) {
    return dp[n];
  }
  for (int i = 2; i <= n; i++) {
    for (int j = 1; j <= i; j++) {
      dp[j] = dp[j] + dp[j - 1] * dp[i - j];
    }
  }
  return dp[n];
}
```

> Time Complexity :
> Space Complexity :

![[Unq_BST.svg]]