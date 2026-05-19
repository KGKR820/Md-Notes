- In this we shall be given an array , arr[0] x arr[1] dimensions of Matrix 1 then arr[1] x arr[2] is dimension of Matrix so on..
- Now we should find min no.of multiplications required to multiply those matrices.
- We shall use a 2D dp array to find that.

```cpp
int Mult(vector<int> &dim) {
  int n = dim.size();
  int dp[n][n];
  
  for (int i = n - 1; i >= 1; i--) {
    for (int j = i; j < n; j++) {
	
      if (i == j) {
        dp[i][j] = 0;
      } else {
        int mini = INT_MAX;
        for (int k = i; k < j; k++) {
          mini =
              min(dp[i][k] + dp[k + 1][j] + dim[i - 1] * dim[k] * dim[j], mini);
        }
		
        dp[i][j] = mini;
      }
    }
  }
  return dp[1][n - 1];
}
```

> Time Complexity :
> Space Complexity :
 