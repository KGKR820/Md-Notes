- In this problem we are given an array of coins(unlimited) , we should the min no.of coins required to sum up a value v.
- We shall use a 1D dp and modify it for every coin one by one to achieve the answer.

```cpp
int change(vector<int> &coins, int amount) {
  int n = coins.size();
  vector<int> dp(amount + 1, amount + 1);
  dp[0] = 0;
  
  for (int i = 0; i < n; i++) {
    for (int j = coins[i]; j <= amount; j++) {
      dp[j] = min(dp[j], dp[j - coins[i]] + 1);
    }
  }
  return dp[amount] > amount ? -1 : dp[amount];
}
```

> Time Complexity :
> Space Complexity :

![[Coin Change.svg]]