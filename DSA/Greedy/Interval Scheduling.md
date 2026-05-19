- In this problem we should find the min number of intervals that should be removed from a list of intervals so that there is no overlapping.
- 1st we shall sort the intervals based on the finish time and loop from start, if start time of interval is less than the finish time of prev interval then it should be discarded and count should be incremented.

```cpp
bool compare(pair<int, int> &a, pair<int, int> &b) {
  return a.second < b.second;
}

int schedule(vector<pair<int, int>> &arr) {
  int n = arr.size();
  int cnt = 0;
  if (arr.empty()) {
    return 0;
  }
  
  sort(arr.begin(), arr.end(), compare);
  int last = arr[0].second;
  
  for (int i = 1; i < n; i++) {
    if (arr[i].first < last) {
      cnt++;
    } else {
      last = arr[i].second;
    }
  }
  return cnt;
}
```

> Time Complexity :
> Space Complexity :