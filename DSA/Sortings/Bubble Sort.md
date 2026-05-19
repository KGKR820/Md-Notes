- Very Basic Sort
- In this we bubble the largest element to the end of the array

```cpp
for(int i=0;i<arr.size()-1;i++){
	for(int j=0;j<arr.size()-i-1;j++){
		if(arr[j] > arr[j+1]){
			swap(arr[j],arr[j+1]);
		}	
	}
}
```

> Time Complexity : O(n<sup>2</sup>)
> Space Complexity : O(1) 

![[Bubble Sort.svg]]


