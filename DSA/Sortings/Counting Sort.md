- It is a non comparison based sorting algorithm 
- It is inefficient if the range of the elements that being sorted is very large

```cpp
int n = arr.size();
int m = -1;

// Find Max element
for (int i : arr) {
   m = max(i, m);
}

vector<int> cntArr(m + 1, 0);

// Frequency input
for (int i : arr) {
   cntArr[i]++;
}

// Prefix Sum
for (int i = 1; i <= m; i++) {
   cntArr[i] += cntArr[i - 1];
}

vector<int> ans(n); // Output array

// Main Sorting
for (int i = n - 1; i >= 0; i--){
   ans[cntArr[arr[i]] - 1] = arr[i];
   cntArr[arr[i]]--;
}
```

> Time Complexity : On+m)
> Space Complexity : On+m)

![[Counting Sort.svg|750]]
