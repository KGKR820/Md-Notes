- Similar to normal 01 Knapsack but here you can pick fraction of any item.
- 1st we shall sort item by their value/weight percentage, then we shall pick the item that has the highest value to weight percentage and pick it if its weight > total wt we will pick only the fraction of it and leave if not we shall move forward until the bag is full.

```cpp
bool compare(pair<int, int> &a, pair<int, int> &b) {
  return (1.0 * a.first) / a.second > (1.0 * b.first) / b.second;
}

double knapsack(vector<int> &item, vector<int> &wt, int capacity) {
  int n = item.size();
  vector<pair<int, int>> arr(n);
  
  for (int i = 0; i < n; i++) {
    arr[i].first = item[i];
    arr[i].second = wt[i];
  }

  sort(arr.begin(), arr.end(), compare);
  double val = 0;
  
  for (int i = 0; i < n; i++) {
    if (arr[i].second < capacity) {
      val += arr[i].first;
      capacity -= arr[i].second;
    } else {
      val += ((1.0 * arr[i].first) / arr[i].second) * capacity;
      break;
    }
  }
  return val;
}
```

> Time Complexity :
> Space Complexity :