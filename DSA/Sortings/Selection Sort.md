- Similar to bubble sort but we shall do only one swap per iteration
- Find the max element in the array and swap the max element with the last element

```cpp
for(int i =0;i<arr.size();i++){
	int mx = INT_MIN;
	for(int j=0;j<arr.size()-i;j++){
		if(arr[j] > mx){
			mx = arr[j];	
		}	
	}
	swap[mx,arr[arr.size()-i-1]];
}
```

> Time Complexity : O(n<sup>2</sup>)
> Space Complexity : O(1) 