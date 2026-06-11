- Complex than [[Merge Sort]] but space efficient 
- A pivot is generated and chosen then around that pivot the array is divided into two parts and then quick sort is again applied on the two divided parts until there is only one element (condn => l<r)
- Here pivot represents a element that is placed correctly in the array

```cpp
int pivot(vector<int> &arr,int left,int right){
	/* 
	// If you wanna use a random ele as a pivot
	
	int pvt = left + rand()%(right-left+1);
	swap(arr[high],arr[pvt]);
	*/
	
	int pvt = arr[right];
	int j = left-1;
	for(int i=left;i<right;i++){
		if(arr[i] < pvt){
			j++;
			swap(arr[i],arr[j]);
		}
	}
	swap(arr[j+1],arr[right]);
	return j+1;
}
void QuickSort(vector<int> &arr,int left,int right){
	if(l<r){
		int pvt = pivot(arr,l,r);
		QuickSort(arr,l,pvt-1);
		QuickSort(arr,pvt+1,r);
	}
}
```

- There are important cases you should remember which are ->
	 1. Choosing the wrong pivot may lead to a complexity of O(n<sup>2</sup>) like if the array is already sorted in correct order dividing into 0 and n-1 parts always.
	 2. Array's containing same elements multiple times.

- To Avoid O(n<sup>2</sup>) we should either random pick the pvt in pivot function (or) use three median rule in which you shall pick arr[left],arr[right],arr[left-(right-left)/2] then you shall assign pvt to the index of the median of those 3.