- The array is divided into two parts 
	 1. Sorted Part (Left)
	 2. Unsorted Part
- The 1st element in unsorted part is chosen as the key and inserted into the sorted part by the swapping the appropriate element in the appropriate place. 
- Efficient for small lists and nearly sorted lists. 

```cpp 
for(int i=1;i<arr.size();i++){
	int key = arr[i];
	int j =i-1;
	while(j>=0 and key < arr[j]){
		arr[j+1] = arr[j];
		j=j--;
	}	
	arr[j+1] = key;
}
```

> Time Complexity : O(n<sup>2</sup>)
> Space Complexity : O(1)