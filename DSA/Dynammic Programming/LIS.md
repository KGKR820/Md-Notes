- Longest increasing sub-sequence , in this we should find longest strictly increasing sub array length.
```cpp
int LIS(vector<int> &arr) {
  int n = arr.size();
  vector<int> lis(n, 1);
  
  for (int i = 1; i < n; i++) {
    for (int prev = 0; prev < i; prev++) {
      if (arr[i] > arr[prev]) {
        lis[i] = max(lis[i], lis[prev] + 1);
      }
    }
  }
  
  int mx = 0;
  for (int i = 0; i < n; i++) {
    mx = max(lis[i], mx);
  }
  return mx;
}
```

> Time Complexity :
> Space Complexity :

![[LIS.svg]]